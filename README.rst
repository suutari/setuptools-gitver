Setuptools Gitver
=================

Simple Git version plugin for setuptools.

Usage
-----

Modify the ``setup.py`` of your project and add ``setuptools-gitver`` to
``setup_requires`` and add keyword argument ``gitver=True``.  Then,
after each release, add ``.post+gitver`` suffix to the version string.

For example, in ``setup.py``::

  import setuptools

  if __name__ == '__main__':
      setuptools.setup(
          name='example-package',
          version='1.2.3.post+gitver',
          setup_requires=['setuptools-gitver'],
          gitver=True,
      )

This will then generate version numbers like 1.2.3.post0.dev7+ga1b2c3d
where 7 is the number of commits since the v1.2.3 tag and a1b2c3d is
commit id of the HEAD.

When creating a release, update the version and remove the
``post+gitver`` suffix.  When there is no ``+gitver`` suffix, the
version won't be touched by Setuptools Gitver.  Also remember to tag the
release in Git with ``git tag -a v1.2.3``.
