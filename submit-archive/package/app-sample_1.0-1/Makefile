# 6Harmonics Inc
# maintainer: Qige Zhao

APP=app-demo

all: $(APP)

$(APP): *.c #include/*.c
	$(CC) $(CFLAGS) $(EXTRA_CFLAGS) -I. -Iinclude -o $@ $^ -L.

clean:
	rm -f $(APP)

