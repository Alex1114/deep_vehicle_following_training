MAIN = $(basename $(wildcard *Main.cpp))
CHECKSTYLE = cpplint --recursive --filter=-build/header_guard .
OBJECTS = $(addsuffix .o, $(filter-out %Main %Test, $(basename $(wildcard *.cpp))))
HEADERS = $(wildcard *.h)
LIBS =  -lcaffe -lopencv_core -lopencv_highgui -lopencv_imgproc -lcuda -lboost_system -lboost_filesystem -lglog
LIBS += -L/home/allen/caffe/build/lib -L/usr/local/cuda/lib
INCDIRS = -I /usr/local/cuda/include -I /home/allen/caffe/.build_release/src/ -I /home/allen/caffe/include
CPPFLAGS = -DUSE_OPENCV

CXX = g++ -g -std=c++11 ${INCDIRS} ${CPPFLAGS}


all:
	make compile

compile: $(MAIN)

checkstyle:
	$(CHECKSTYLE) *.cpp *.h

%Main: %Main.o $(OBJECTS)
	$(CXX) -o $@ $^ $(LIBS)

%.o: %.cpp
	$(CXX) -c $<

clean:
	rm -f *.o
	rm -f $(MAIN)
	rm -f $(TEST)
