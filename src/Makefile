#   Dex Repair
#   -----------------------------------------
#
#   Anestis Bechtsoudis <anestis@census-labs.com>
#   Copyright 2015-2016 by CENSUS S.A. All Rights Reserved.
#
#   Licensed under the Apache License, Version 2.0 (the "License");
#   you may not use this file except in compliance with the License.
#   You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
#   Unless required by applicable law or agreed to in writing, software
#   distributed under the License is distributed on an "AS IS" BASIS,
#   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#   See the License for the specific language governing permissions and
#   limitations under the License.

# Default to gcc
CC ?= gcc

TARGET  = dexRepair
CFLAGS  += -c -std=c11 -D_GNU_SOURCE \
           -Wall -Wextra -Werror
LDFLAGS += -lm -lz

.PHONY: default all clean

default: $(TARGET)
all: default

OBJECTS = $(patsubst %.c, %.o, $(wildcard *.c))
HEADERS = $(wildcard *.h)

%.o: %.c $(HEADERS)
	$(CC) $(CFLAGS) -c $< -o $@

.PRECIOUS: $(TARGET) $(OBJECTS)

$(TARGET): $(OBJECTS)
	$(CC) $(OBJECTS) $(LDFLAGS) -o $@
	cp $(TARGET) ../bin/$(TARGET)

clean:
	-rm -f *.o
	-rm -f $(TARGET)
