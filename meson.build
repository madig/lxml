project(
    'lxml',
    'c', 'cython',
    meson_version: '>= 1.0.0',
    default_options: [
        'buildtype=release',
    ]
)

fs = import('fs')
py = import('python').find_installation(pure: false)
dep_py = py.dependency()
dep_libxml2 = dependency('libxml-2.0', static: true)
dep_libxslt = dependency('libxslt', static: true)
cython = find_program('cython')

lxml_includes = include_directories('src/lxml/includes')

# https://github.com/mesonbuild/meson/discussions/11578
# py.extension_module(
#     'lxml',
#     'src/lxml/_elementpath.py',
#     'src/lxml/builder.py',
#     'src/lxml/etree.pyx',
#     'src/lxml/html/clean.py',
#     'src/lxml/html/diff.py',
#     'src/lxml/objectify.pyx',
#     'src/lxml/sax.py',
#     dependencies: [dep_py, dep_libxml2, dep_libxslt],
#     include_directories: [lxml_includes],
#     install: true
# )

# TODO: generate lxml-version.h

subdir('src/lxml')
subdir('src/lxml/html')
