dump_exec = executable(
    'dump-yaml',
    sources: 'dump-yaml.c',
    include_directories: libglib_yaml_inc,
    dependencies: libglib_yaml_dep,
)

parse_exec = executable(
    'parse-yaml',
    sources: 'parse-yaml.c',
    include_directories: libglib_yaml_inc,
    dependencies: libglib_yaml_dep,
)

find_node_exec = executable(
    'find-node',
    sources: 'find-node.c',
    include_directories: libglib_yaml_inc,
    dependencies: libglib_yaml_dep,
)
test ('Find node test', find_node_exec, args: ['../examples/example-0.yml', 'title'])

example_files = files(
  '../examples/ex-alias.yml',
  '../examples/example-0.yml',
  '../examples/example-1.yml',
  '../examples/example-2.yml',
  '../examples/example-3.yml',
  '../examples/ex-comments.yml',
  '../examples/ex-complex-mapping.yml',
  '../examples/ex-documents-with-end.yml',
  '../examples/ex-documents.yml',
  '../examples/ex-explicit-tags.yml',
  '../examples/ex-folded-scalar.yml',
  '../examples/ex-global-tags.yml',
  '../examples/ex-indent-scalars.yml',
  '../examples/ex-literal-scalar.yml',
  '../examples/ex-map-maps.yml',
  '../examples/ex-map-scalar-scalar.yml',
  '../examples/ex-map-scalar-sequence.yml',
  '../examples/ex-multiline-scalars.yml',
  '../examples/ex-nested-map.yml',
  '../examples/ex-ordered-map.yml',
  '../examples/ex-plain-scalar.yml',
  '../examples/ex-quoted-scalars.yml',
  '../examples/ex-sequence-maps.yml',
  '../examples/ex-sequence-scalars.yml',
  '../examples/ex-sequence-sequences.yml',
  '../examples/ex-unordered-set.yml',
)

foreach t : example_files
    test ('Dump test', dump_exec, args: [t])
    test ('Parse test', parse_exec, args: [t])
endforeach

broken_file = files (
  '../examples/ex-broken.yml',
)

test ('Dump test', dump_exec, args: [broken_file], should_fail: false)
test ('Parse test', parse_exec, args: [broken_file], should_fail: true)
