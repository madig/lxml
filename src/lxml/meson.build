cython_files = [
    '_elementpath.py',
    'builder.py',
    'etree.pyx',
    'objectify.pyx',
    'sax.py',
]

foreach cython_file: cython_files
    cython_target = custom_target(
        input: cython_file,
        output: fs.replace_suffix(cython_file, '.c')  ,
        command: [cython, '-3', '@INPUT@', '-o', '@OUTPUT@']
    )

    py.extension_module(
        fs.stem(cython_file),
        cython_target,
        dependencies: [dep_py, dep_libxml2, dep_libxslt],
        include_directories: [lxml_includes],
        install: true
    )
endforeach
