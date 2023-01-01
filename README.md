## OpenCV: Open Source Computer Vision Library

### Resources

* Homepage: <https://opencv.org>
  * Courses: <https://opencv.org/courses>
* Docs: <https://docs.opencv.org/4.x/>
* Q&A forum: <https://forum.opencv.org>
  * previous forum (read only): <http://answers.opencv.org>
* Issue tracking: <https://github.com/opencv/opencv/issues>
* Additional OpenCV functionality: <https://github.com/opencv/opencv_contrib> 


### Contributing

Please read the [contribution guidelines](https://github.com/opencv/opencv/wiki/How_to_contribute) before starting work on a pull request.

#### Summary of the guidelines:

* One pull request per issue;
* Choose the right base branch;
* Include tests and documentation;
* Clean up "oops" commits before submitting;
* Follow the [coding style guide](https://github.com/opencv/opencv/wiki/Coding_Style_Guide).


###Usman Wyne Additional notes
* To build this on windows I found a great article here. 
https://cv-tricks.com/how-to/installation-of-opencv-4-1-0-in-windows-10-from-source/

There only additional things that I had to do to successfully run the python code was 
When I finished it however then I got the following errors
>>> import cv2
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
ModuleNotFoundError: No module named 'cv2'

To fix this error I had to do the following. I suspect that there could be a redundant step in between, but they worked.
1. Added BUILD_opencv_python3 as a boolean variable as it was not there for me in CMAKE by default
2. Added BUILD_opencv_python_bindings_generator as a boolean

3. Next I searched under the build folder to find numpy path and added that in there for PYTHON3_NUMPY_INCLUDE_DIRS


it was build/python_loader/lib/site-packages/numpy-1.24.1-py3.10-win-amd64.egg/numpy/core/include.

4. Once all that was done, then I pressed configure and then pressed Generate.

5. The last step is to move the built python code to your python install's \Lib\site-packages
so to do that you go to folder \build\python_loader in command prompt and then run the following
python setup.py install --prefix= <the path="" where="" python.exe="" exists="">

it will complain about deprecated methods etc, but by and large should run without issues, if your compilation earlier was correct and now when you would import cv2 again then it would show it correctly


