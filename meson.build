project(
    'lxml',
    'c', 'cython',
    meson_version: '>= 1.0.0',
)

py = import('python').find_installation(pure: false)
dep_py = py.dependency()
dep_libxml2 = dependency('libxml-2.0', static: true)
dep_libxslt = dependency('libxslt', static: true)

py.extension_module(
    'lxml',
    'src/lxml/etree.pyx',
    'src/lxml/objectify.pyx',
    dependencies : [dep_py, dep_libxml2, dep_libxslt],
    install: true
)
