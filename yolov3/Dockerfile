FROM ubuntu:18.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    git \
    make \
    gcc \
    wget \
    libopencv-dev \
    pkg-config \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir /darknet
WORKDIR /darknet

RUN git clone https://github.com/pjreddie/darknet .

RUN make

RUN wget https://pjreddie.com/media/files/yolov3.weights

ENTRYPOINT [ "/bin/sh", "-c", "wget -q -O input.jpg \"$1\" && ./darknet detector test cfg/coco.data cfg/yolov3.cfg yolov3.weights input.jpg", "/bin/sh" ]

CMD ["https://raw.githubusercontent.com/pjreddie/darknet/master/data/dog.jpg"]