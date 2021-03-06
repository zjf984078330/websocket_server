SRC_SERVER_DIR = ../src/server
SRC_CLIENT_DIR = ../src/client
BOOST_DIR = ../external/boost
POCO_DIR = ../external/poco
GTEST_DIR = ../external/gtest-1.8.0

SRCS_SERVER = queue.cpp \
	websocket_connection.cpp \
	page_connection.cpp \
	request_handler_factory.cpp \
	websocket_server.cpp \
	server_main.cpp

SRCS_CLIENT = client_msg.cpp \
	websocket_client.cpp \
	backend_test.cpp \
	connection_test.cpp \
	run_server_tests.cpp

OBJS_SERVER = $(SRCS_SERVER:.cpp=.o)

OBJS_CLIENT = $(SRCS_CLIENT:.cpp=.o)

EXEC_SERVER = server

EXEC_CLIENT = client

CFLAGS = -g -std=c++11 -I$(SRC_SERVER_DIR)

CFLAGS += -I$(BOOST_DIR)/include/

CFLAGS += -I$(POCO_DIR)/include/

CFLAGS += -I$(GTEST_DIR)/include/

LDFLAGS = -L$(BOOST_DIR)/lib -lboost_date_time  -lboost_system  -lboost_thread

LDFLAGS = -L$(POCO_DIR)/lib -lPocoUtil -lPocoXML -lPocoJSON -lPocoNet -lPocoFoundation

LDFLAGS += -L$(GTEST_DIR)/lib -lgtest  -ldl -lpthread 

vpath %.cpp ../src/server ../src/client

all: $(EXEC_SERVER) $(EXEC_CLIENT)

$(EXEC_SERVER): $(OBJS_SERVER)
	g++ -o $@ $(OBJS_SERVER) $(CFLAGS) $(LDFLAGS)

$(EXEC_CLIENT): $(OBJS_CLIENT)
	g++ -o $@ $(OBJS_CLIENT) $(CFLAGS) $(LDFLAGS)

.cpp.o:
	g++ $(CFLAGS) -c $<

clean:
	rm -f $(OBJS_SERVER) $(OBJS_CLIENT) *~ $(EXEC_SERVER) $(EXEC_CLIENT)

