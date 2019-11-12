project(
  'libyaml-glib', 'c',
  version: '1.0.0',
  license: 'GPL3',
  default_options: 'buildtype=debugoptimized',
  meson_version: '>= 0.49.0',
)

project_name = meson.project_name()

project_version = meson.project_version()
version_array = project_version.split('.')
major_version = version_array[0].to_int()
minor_version = version_array[1].to_int()
micro_version = version_array[2].to_int()

libglib_yaml_inc = include_directories('libglib-yaml')

gobject_introspection_dep = dependency('gobject-introspection-1.0', version: '>= 1.0')
yaml_dep = dependency('yaml-0.1', version: '>= 0.1')

subdir('libglib-yaml')
subdir('test')

enable_gtk_doc = get_option('gtk_doc')
if enable_gtk_doc
  subdir('doc')
endif

enable_man = get_option('man')
if enable_man
  subdir('man')
endif

cc = meson.get_compiler('c')
source_root = meson.current_source_dir()

output = '\nConfiguration:\n\n'
output += '\tCompiler:                ' + cc.get_id() + '\n'
output += '\tSource code location:    ' + source_root + '\n'
output += '\tIntrospection Data:      ' + enable_introspection.to_string() + '\n\n'
output += '\tBuild Reference Manual:  ' + enable_gtk_doc.to_string() + '\n'
output += '\tBuild Manual Pages:      ' + enable_man.to_string()
message(output)

