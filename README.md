# Search engine
Final work on the course "C++ Developer" from [Skillbox](https://skillbox.ru).

## Description
How a search engine works:
- In the configuration file [`config.json`](https://github.com/alexander-rodin42/search_engine/blob/main/config.json), before starting the application, the names of the files that the engine will search for are set.
- The search engine independently bypasses all files and indexes them like this. to find the most relevant documents for any search query.
- The user sets a request through a JSON file [`requests.json`](https://github.com/alexander-rodin42/search_engine/blob/main/requests.json). The query consists of words for which you need to find documents.
- The request is converted into a list of unique words. Compiles a list of documents that contain these words.
- Search results are ranked, sorted and given to the user.
- At the end, the program generates a file `answers.json`, writes the search results into it.

## Tech
Search engine uses a number of open source projects to work properly:
- To read/generate JSON documents, a third-party library [nlohmann/json](https://github.com/nlohmann/json) is used.
- For unit tests, the [GoogleTest](https://github.com/google/googletest) library is used.

## Instruction

To build the project to be installed:
- [CMake](https://cmake.org/download/) build system.
- [MVS](https://visualstudio.microsoft.com/ru/downloads/) or [MinGW-w64](https://www.mingw-w64.org/downloads/#mingw-builds) compiler.

### Project build

<details>
<summary> - Building using the Windows command line:</summary>
<br>

- From the command line, navigate to the project's root directory `C:\...\search_engine` and create a build directory:

  ```sh
  mkdir build
  ```
- Next, navigate to the build directory and run CMake to configure the project and generate a native build system:

  ```sh
  cd build
  cmake ..
  ```

- Then call that build system to actually compile/link the project:

  ```sh
  cmake --build .
  ```

- Upon completion of the compilation process, the executable file `search_engine.exe` will appear in the `..\search_engine\build` folder if you are using the MinGW-w64 compiler, and `..\search_engine\build\Debug` for MVS compiler.

</details>

### Launch preparation

- For the program to work correctly, it is necessary that the executable file be in the same directory as the files: [`config.json`](https://github.com/alexander-rodin42/search_engine/blob/main/config.json), [`requests.json`](https://github.com/alexander-rodin42/search_engine/blob/main/requests.json).

- In order for the search engine to process custom documents, add the path to this document to the "files" list in [`config.json`](https://github.com/alexander-rodin42/search_engine/blob/main/config.json):
 ```sh
 {"files":["resources\\file001.txt", ... ,"user\\custom_document.txt",]}
 ```
 > Note: By default, paths to files from the [`resources`](https://github.com/alexander-rodin42/search_engine/tree/main/resources) folder are specified. The executable and the `resources` folder must be in the same directory.


- The [`requests.json`](https://github.com/alexander-rodin42/search_engine/blob/main/requests.json) file contains custom requests:
 ```sh
 {"requests":[""request1","request2","request3"]}
 ```
 > Note: The request can only contain Latin characters.

- The number of responses depends on the "max_responses" parameter, the default is 5. You can change the value in [`config.json`](https://github.com/alexander-rodin42/search_engine/blob/main/config.json).
