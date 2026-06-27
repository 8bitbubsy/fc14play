# fc14play
Aims to be an accurate C port of Future Composer v1.4's internal replayer. \
The project contains example code in the fc14play folder on how to interface with the API. \
This is a direct port of the original tracker source codes.

# Notes
- This player is not optimized for speed, it's optimized for accuracy and sound quality
- To compile fc14play (the test program) on macOS/Linux, you need SDL2
- When compiling, you need to pass the driver to use as a compiler pre-processor definition (f.ex. AUDIODRIVER_WINMM, check "paula.h")
