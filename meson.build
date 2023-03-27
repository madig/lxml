project(
    'lxml',
    'c', 'cython',
    meson_version: '>= 1.0.0',
)

py = import('python').find_installation(pure: false)
dep_py = py.dependency()
dep_libxml2 = dependency('libxml-2.0', static: true)
dep_libxslt = dependency('libxslt', static: true)
cython = find_program('cython')

cython_files = [
    'src/lxml/_elementpath.py',
    'src/lxml/builder.py',
    'src/lxml/etree.pyx',
    'src/lxml/html/clean.py',
    'src/lxml/html/diff.py',
    'src/lxml/objectify.pyx',
    'src/lxml/sax.py',
]

foreach cython_file: cython_files
    cython_target = custom_target(
        input: cython_file,
        output: fs.replace_suffix(cython_file, '.c')  ,
        command: [cython, '-3', '@INPUT@', '-o', '@OUTPUT@']
    )

    py3.extension_module(
        fs.stem(cython_file),
        cython_target,
        dependencies: [dep_py, dep_libxml2, dep_libxslt],
        include_directories: ['src/lxml/includes'],
        install: true
    )
endforeach

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
#     include_directories: ['src/lxml/includes'],
#     install: true
# )

# TODO: generate lxml-version.h
