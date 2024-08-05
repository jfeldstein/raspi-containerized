FROM ubuntu:latest

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    wget \
    git \
    build-essential \
    libusb-1.0-0-dev \
    libcups2-dev \
    cups \
    avahi-daemon \
    avahi-utils \
    dbus \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*


COPY ./cupsd.conf /etc/cups/cupsd.conf
COPY ./lw450tt.ppd /etc/cups/ppd/lw450tt.ppd

COPY ./airprint.service /etc/avahi/services/airprint.service

CMD ["sh", "-c", "/etc/init.d/dbus start && /etc/init.d/avahi-daemon start && /etc/init.d/cups start && tail -f /dev/null"]

