git clone https://github.com/ggerganov/llama.cpp

cd /app/llama.cpp
rm -rf build
mkdir build && cd build
cmake -DLLAMA_CURL=OFF ..
cmake --build . --config Release

Mac
./bin/llama-cli -m ../../app/models/gpt-oss-20b-Q4_K_M.gguf -i --color --simple-io

WSL
./llama.cpp/build/bin/llama-cli -m app/models/gpt-oss-20b-Q4_K_M.gguf -i --color --simple-io -t 16