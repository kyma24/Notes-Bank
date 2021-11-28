-   packaging(1)
    
    in Python, the term **packaging** refers to putting modules that have been written in a standard format, so that other programmers can install and use them with ease.
    
    This involves the use of the modules **setuptools** and **distutils**.
    
    The first step in packaging is to organize existing files correctly. Place all the files you want to put in a library in the same parent directory. This directory should also contain a file called ****init**.py**, which can be blank but must be present in the directory. ← this makes it a package
    
    The directory goes into another directory containing the readme and license, as well as an important file called **[setup.py](http://setup.py)**.
    
    ```python
    #i.e.
    Sololearn/
    	LICENSE.txt
    	README.txt
    	setup.py
    	sololearn/
    		__init__.py
    		sololearn.py
    		sololearn2.py
    ```
    
    can place as many script files in the directory as needed.
    
-   packaging(2)
    
    the next step in packaging is to write the **[setup.py](http://setup.py)** file.
    
    This contains information necessary to assemble the package so it can be uploaded to **PyPI** and installed with **pip**(name, version, etc.).
    
    Example of a [setup.py](http://setup.py) file:
    
    ```python
    from distutils.core import setup
    
    setup(
    	name = 'Sololearn',
    	version = '0.1dev',
    	packages = ['sololearn',],
    	license = 'MIT',
    	long_description = open('README.txt').read(),
    )
    ```
    
    after creating this **[setup.py](http://setup.py)** file, upload it to **PyPI**, or use the command line to create a binary distribution(an executable installer).
    
    To build a source description, use the command line to navigate to the directory containing [setup.py](http://setup.py), and run the command **python [setup.py](http://setup.py) sdist**. Run **python [setup.py](http://setup.py) bdist** or, for Windows, **python [setup.py](http://setup.py) bdist.wininst** to build a binary distribution.
    
    Use **python [setup.py](http://setup.py) register**, followed by **python [setup.py](http://setup.py) sdist upload** to upload a package.
    
    Finally, install a package with **python [setup.py](http://setup.py) install**.
    
-   packaging for users
    
    many computer users who aren't programmers don't have Python installed. Therefore, it is useful to package scripts as executable files for the relevant platform such as the Windows or Mac operating systems. This isn't necessary for Linux, as most Linux users have Python installed, and are able to run scripts as they are.
    
    For Windows, many tools are available for converting scripts to executables. For example, **py2exe**, can be used to package a Python script, along with the libraries it requires, into a single executable.
    
    **PyInstaller** and **cx\_Freeze** serve the same purpose.
    
    For Macs, use **py2app**, **PyInstaller** or **cx\_Freeze**.