# macOS Development Setup

A macOS development environment setup guide and installation scripts.

![Release-macOS-doc][release-macos-shield] [![License][license-shield]](LICENSE.md) [![Twitter][twitter-shield]](https://twitter.com/mgomesborges)

## Command Line Tools (mandatory)

![Command Line Tools](./assets/terminal.png?raw=true)

The Command Line Tools Package is a small self-contained package available for download separately from Xcode and that allows you to do command line development in macOS.

### Install Command Line Tools

1. Paste that in the terminal prompt:

    ```bash
    xcode-select --install
    ```

2. A software update popup window will appear. Click `Install`, then agree to the Terms of Service when requested.

    ![Command Line Tools](./assets/Xcode-command-line-tools.png)

3. The Command Line Tools is installed at:

    ```bash
    /Library/Developer/CommandLineTools/
    ```

## Xcode (optional)

![Xcode](./assets/Xcode.png)

[Xcode](https://developer.apple.com/xcode/) is Apple's integrated development environment (IDE) for Swift, Objective-C, C, and C++. It also supports Java, AppleScript, Python, Ruby, and ResEdit (Rez).

### Install Xcode

Download and install Xcode from the [App Store](https://apps.apple.com/us/app/xcode/id497799835?mt=12) or from [Apple's website](https://developer.apple.com/xcode/)

:warning: Xcode takes over 13 GB of disk space. Its installation is not mandatory.

## Homebrew (mandatory)

![Homebrew](./assets/homebrew.png?raw=true)

[Homebrew](https://brew.sh) is the missing package manager for macOS.

### Install Homebrewv

Open the terminal and run the following script:

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## Git (mandatory)

![Git](./assets/git.png?raw=true)

[Git](https://git-scm.com) is a free and open source distributed version control system.

### Install Git

Run on the terminal:

```bash
brew install git
```

### Configure Git

Paste that in the terminal:

```bash
git_config_global() {
    printf "\nGit configuration - Ctrl+C to cancel\n"

    printf "\nUser name (example: M Gomes-Borges) : "
    read -r GIT_USER_NAME

    printf "\nE-mail (example: git@gomes-borges.com): "
    read -r GIT_USER_EMAIL

    # Set git user name and email
    git config --global user.name "${GIT_USER_NAME}"
    git config --global user.email "${GIT_USER_EMAIL}"

    # Set git terminal colors
    git config --global color.ui true
    git config --global color.status.changed "blue normal"
    git config --global color.status.untracked "red normal"
    git config --global color.status.added "magenta normal"
    git config --global color.status.updated "green normal"
    git config --global color.status.branch "yellow normal bold"
    git config --global color.status.header "white normal bold"

    printf "\nGit setup completed\n"
}

git_config_global
```

### Check Git configuration

Check your name and e-mail:

```bash
git config --global --list

# user.name=Your User Name
# user.email=your@email.com
# ...
```

## Terminal

![Zsh](./assets/oh-my-zsh-logo.png?raw=true) ![Bash](./assets/bash-logo.png?raw=true)

With macOS Catalina - October 2019, Apple is now using Zsh as the default shell. However, you can quickly switch back to Bash if you prefer.

Check out how to select your shell and set up your terminal theme:

* [Bash tutorial](./docs/terminal-bash-setup.md)
* [Zsh tutorial](./docs/terminal-zsh-setup.md)

## Python

![Python](./assets/python.png?raw=true)

[Python](https://www.python.org) is a programming language that lets you work quickly
and integrate systems more effectively.

### Install Pyenv

[Pyenv](https://github.com/pyenv/pyenv) lets you easily switch between multiple versions of Python. It's simple:

1. Install pyenv:

    ```bash
    brew install pyenv
    ```

2. Install pyenv-virtualenvwrapper :

    ```bash
    brew install pyenv-virtualenvwrapper
    ```

### Install Python

1. Init Pyenv:

    ```bash
    eval "$(pyenv init -)"
    ```

2. List the available Python versions:

    ```bash
    pyenv install --list
    ```

3. Install the Python versions you want using the example below:

    ```bash
    # Python 3.6.10
    PYTHON_CONFIGURE_OPTS="--enable-framework" pyenv install 3.6.10

    # Python 3.7.6
    PYTHON_CONFIGURE_OPTS="--enable-framework" pyenv install 3.7.6

    # Python 3.8.1
    PYTHON_CONFIGURE_OPTS="--enable-framework" pyenv install 3.8.1
    ```

### Set the Python version you want as default

1. Set the default Python version:

    ```bash
    pyenv global 3.6.10
    ```

2. Set up the virtualenvwrapper:

    ```bash
    pyenv virtualenvwrapper
    ```

## Python for Data Science

![Python Package](./assets/python-package.png?raw=true)

[Python set-up guide](./docs/python-setup.md) will help to install Python libraries used by data scientists:

* TensorFlow
* Keras
* numpy
* pandas
* scipy
* pillow
* scikit-learn
* scikit-image
* sk-video
* Matplotlib
* Jupyter lab & extensions

## Visual Studio Code - VS Code

![VS Code](./assets/vs-code.png?raw=true)

[Visual Studio Code](https://code.visualstudio.com/) is a lightweight but powerful source code editor.

Check out the [VS Code set-up guide](./docs/vs-code.md).

![LaTeX with VSCode](./assets/vs-code-latex.png?raw=true)

## LaTeX - MacTeX (optional)

![LaTeX](./assets/mactex.png?raw=true)

[MacTeX](https://tug.org/mactex/mactex-download.html) is an install package which installs everything needed to run TeX on Mac OS X.

### Install LaTeX

1. Install Ghostscript

    ```bash
    brew install ghostscript
    ```

2. Download MacTeX 2019 from <https://tug.org/mactex/mactex-download.html>

3. Double click on the downloaded file to install
4. Several pages of information will be displayed
5. One of the last is shown below. Click on the `Customise` button

    ![MacTex](./assets/mactex-installation01.png?raw=true)

6. Deselect the packages `GUI-Applications` and `Ghostscript`, then click on `Install`

    ![MacTex](./assets/mactex-installation02.png?raw=true)

## Qt

![Qt](./assets/qt.png?raw=true)

[Qt](https://www.qt.io) is a cross-platform application development framework for desktop, embedded and mobile using C++ or Python. Supported Platforms include Linux, OS X, Windows, VxWorks, QNX, Android, iOS, BlackBerry, Sailfish OS and others.

![Qt](./assets/qt-creator.png?raw=true)

### Install Qt

1. Download and run the [Qt online Installer](https://www.qt.io/download-qt-installer)
2. Click `Next` on the Welcome to the Qt Online installer window
3. Click `Skip` on the Qt Account window
4. Accept the Qt Open Source Usage Obligations, and click `Continue`
5. Click `Continue` no the Setup - Qt window
6. The installer will complain that Xcode is not installed, just click `OK`
7. On the Qt Creator User Experience Development window, make your choice and click `Continue`
8. Click `Continue` on the Installation Folder window
9. Select the latest Qt version prebuilt components:
   * [x] `Qt 5.14.0` / `macOS`
   * [x] `Developer and Designer Tools` / `Qt Installer Framework 3.2`
10. Then click `Next` and `Install`

### Add Qt Creator into Applications

Paste that in the terminal prompt:

```bash
# Symbolic link
ln -s "${HOME}/Qt/Qt Creator.app" "/Applications"
```

## FFmpeg

![FFmpeg](./assets/ffmpeg.png?raw=true)

[FFmpeg](https://ffmpeg.org/documentation.html) is a complete, cross-platform solution to record, convert and stream audio and video.

### Install FFmpeg

Run that in the terminal:

```bash
# Leave Python virtual environment
deactivate

# Install FFmpeg with all modules
brew install ffmpeg
```

## OpenCV

![FFmpeg](./assets/opencv.png?raw=true)

[OpenCV](https://opencv.org) (Open Source Computer Vision Library) is an open source computer vision and machine learning software library.

### Install OpenCV with Python and Qt support

Use Python 3.7.6 to keep compatibility. Check [how to install Python 3.7.6](#install-python).

1. Create a Python virtual environment with NumPy:

    ```bash
    pyenv shell 3.7.6
    mkvirtualenv opencv
    pip install --upgrade pip
    pip install numpy==1.18.1
    deactivate
    ```

2. Installing Opencv dependencies

    ```bash
    brew install cmake pkg-config ceres-solver eigen ffmpeg glog \
                 harfbuzz jpeg libpng libtiff openexr tbb
    ```

3. Download OpenCV

    ```bash
    OPENCV_VERSION="4.2.0"

    # Clone OpenCV project from GitHub
    git clone https://github.com/opencv/opencv "${HOME}/opencv"

    # Clone OpenCV extra modules from GitHub
    git clone https://github.com/opencv/opencv_contrib "${HOME}/opencv_contrib"

    # Create a branch from last stable version
    cd "${HOME}/opencv"
    git checkout tags/${OPENCV_VERSION} -b ${OPENCV_VERSION}

    # Create a branch from last stable version
    cd "${HOME}/opencv_contrib"
    git checkout tags/${OPENCV_VERSION} -b ${OPENCV_VERSION}

    # Create a build directory
    mkdir "${HOME}/opencv/build"
    ```

4. Configure OpenCV

    ```bash
    # Qt PATH
    if ls ${HOME}/Qt*/*/clang_64/bin/qmake 1>/dev/null 2>&1; then
        QT_ON_OFF=ON
    else
        QT_ON_OFF=OFF
    fi

    QT_LIB=$(echo ${HOME}/Qt*/*/clang_64/lib/cmake)
    QT_QMAKE=$(echo ${HOME}/Qt*/*/clang_64/bin/qmake)

    # Python PATH
    pyenv shell 3.7.6
    workon opencv
    py3_exec=$(which python)
    py3_config=$(python -c "from distutils.sysconfig import get_config_var as s; print(s('LIBDIR'))")
    py3_include=$(python -c "import distutils.sysconfig as s; print(s.get_python_inc())")
    py3_packages=$(python -c "import distutils.sysconfig as s; print(s.get_python_lib())")
    py3_numpy=$(python -c "import numpy; print(numpy.get_include())")
    ```

    ```bash
    cd "${HOME}/opencv/build"
    pyenv shell 3.7.6
    workon opencv

    # Configure OpenCV via CMake
    cmake -D CMAKE_BUILD_TYPE=RELEASE \
          -D CMAKE_INSTALL_PREFIX="/usr/local" \
          -D OPENCV_EXTRA_MODULES_PATH="${HOME}/opencv_contrib/modules" \
          -D ENABLE_PRECOMPILED_HEADERS=OFF \
          -D OPENCV_GENERATE_PKGCONFIG=ON \
          -D WITH_CUDA=OFF \
          -D WITH_QT="${QT_ON_OFF}" \
          -D CMAKE_PREFIX_PATH="${QT_LIB}" \
          -D QT_QMAKE_EXECUTABLE="${QT_QMAKE}" \
          -D QT5Core_DIR="${QT_LIB}/Qt5Core" \
          -D QT5Gui_DIR="${QT_LIB}/Qt5Gui" \
          -D QT5Test_DIR="${QT_LIB}/Qt5Test" \
          -D QT5Widgets_DIR="${QT_LIB}/Qt5Widgets" \
          -D Qt5Concurrent_DIR="${QT_LIB}/Qt5Concurrent" \
          -D OPENCV_ENABLE_NONFREE=ON \
          -D WITH_GTK=OFF \
          -D WITH_OPENGL=ON \
          -D WITH_OPENVX=ON \
          -D WITH_OPENCL=ON \
          -D WITH_TBB=ON \
          -D WITH_EIGEN=ON \
          -D WITH_GDAL=ON \
          -D WITH_FFMPEG=ON \
          -D BUILD_TIFF=ON \
          -D BUILD_opencv_python2=OFF \
          -D BUILD_opencv_python3=ON \
          -D PYTHON_DEFAULT_EXECUTABLE="${py3_exec}" \
          -D PYTHON3_EXECUTABLE="${py3_exec}" \
          -D PYTHON3_INCLUDE_DIR="${py3_include}" \
          -D PYTHON3_PACKAGES_PATH="${py3_packages}" \
          -D PYTHON3_LIBRARY="${py3_config}" \
          -D PYTHON3_NUMPY_INCLUDE_DIRS="${py3_numpy}" \
          -D INSTALL_PYTHON_EXAMPLES=ON \
          -D INSTALL_C_EXAMPLES=ON \
          -D BUILD_EXAMPLES=ON \
          -D CMAKE_CXX_STANDARD=14 ..
    ```

5. Make & make install

    ```bash
    cd "${HOME}/opencv/build"
    pyenv shell 3.7.6
    workon opencv

    make -j 4
    ```

    ```bash
    sudo make -j 4 install
    ```

### Test OpenCV installation with Python

```bash
workon opencv
python -c "import cv2;  print(cv2.__version__)"
```

### Test OpenCV installation with C++

We can run some sample code located at `opencv/samples/cpp`:

```bash
cd "${HOME}/opencv/samples/cpp"
workon opencv

g++ -std=c++11 $(pkg-config --cflags --libs opencv4) facedetect.cpp -o ${TMPDIR}/test

${TMPDIR}/test
```

### Test OpenCV installation with Qt

1. Add `:/usr/local/bin` to PATH

    Go to **Project**, expand **Build Environment** and add `:/usr/local/bin` to PATH.

2. Add a new variable called `PKG_CONFIG_PATH` with the value `/usr/local/lib/pkgconfig`

    ![Qt build settings for OpenCV](./assets/qt-path.png?raw=true)

3. Add a few lines to the project file `.pro` to tell qmake to use pkg-config for OpenCV:

    ```bash
    # Set up Qmake to use pkg-config
    QT_CONFIG -= no-pkg-config
    CONFIG += link_pkgconfig
    PKGCONFIG += opencv4

    # Add OpenCV Libraries
    LIBS += $(pkg-config --libs opencv4)
    ```

4. You may receive a runtime error similar to the message below:

    ```bash
    dyld: Symbol not found: __cg_jpeg_resync_to_restart
    Referenced from: /System/Library/Frameworks/ImageIO.framework/Versions/A/ImageIO
    Expected in: /usr/local/lib/libJPEG.dylib
    in /System/Library/Frameworks/ImageIO.framework/Versions/A/ImageIO
    The program has unexpectedly finished.
    ```

    **To fix it**, go to `Project` -> `Run` -> `Run Environment` -> Unset `DYLD_LIBRARY_PATH`.

    ![DYLD problem](./assets/qt-dyld.png?raw=true)

### Sym-link OpenCV to a virtual environment (if necessary)

1. Activate the TARGET Python virtual environment:

    ```bash
    workon TARGET_ENV
    ```

2. Create a symbolic link to OpenCV:

    ```bash
    # Get the OpenCV library path
    opencv_lib=$(echo ${HOME}/opencv/build/lib/python3/*.so)

    # Get the site-packages path of the virtual environment
    site_packages=$(python3 -c "import distutils.sysconfig as s; print(s.get_python_lib())")

    # Create a symbolic link to OpenCV library
    ln -s ${opencv_lib} ${site_packages}
    ```

## Contributing

All contributions are welcome! There are many ways in which you can participate in the project, for example:

* [Submit bugs and feature requests](https://github.com/mgomesborges/mac-dev-setup/issues)
* Review the documentation and make pull requests for anything from typos to new content

If you are interested in fixing issues and contributing directly to the code base, please read our [Contribution Guide](CONTRIBUTING.md).

## Feedback

* [Request a new feature](CONTRIBUTING.md)
* [File an issue](https://github.com/mgomesborges/mac-dev-setup/issues)
* Ask a question on [Twitter](https://twitter.com/mgomesborges)

## Author

* [Marcos Gomes-Borges](https://github.com/mgomesborges)

## License

The source code is licensed under the [MIT license](LICENSE.md).

The content of this project itself is licensed under the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0).

[twitter-shield]: https://img.shields.io/twitter/follow/mgomesborges?label=Follow&style=social
[release-macos-shield]: https://img.shields.io/badge/Doc-18--Jan--2020-blue
[license-shield]: https://img.shields.io/github/license/mgomesborges/mac-dev-setup.svg
