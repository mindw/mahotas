=========================
Input/Output with Mahotas
=========================

Mahotas does not have any builtin support for input/output. However, it wraps a
few other libraries that do. The result is that you can do::

    import mahotas as mh
    image = mh.imread('file.png')
    mh.imwrite('copy.png', image)

It can use the following backends (it tries them in the following order):

1.  It prefers `imread <https://github.com/luispedro/imread>`__, if it is
    available. Imread is a native C++ library which reads images into Numpy
    arrays. It supports PNG, JPEG, TIFF, WEBP, BMP, and a few TIFF-based
    microscopy formats (LSM and STK).

2.  It also looks for `freeimage <http://freeimage.sourceforge.net/>`__.
    Freeimage can read and write many formats. Unfortunately, it is harder to
    install and it is not as well-maintained as imread.

3.  As a final fallback, it tries to use `matplotlib
    <http://matplotlib.org/>`__, which has builtin PNG support and wraps PIL
    for other formats.

