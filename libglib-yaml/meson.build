headers = files(
	'glib-yaml-parser.h',
	'glib-yaml-stream.h',
	'glib-yaml-document.h',
	'glib-yaml-node.h',
)

sources = files(
	'glib-yaml-parser.c',
	'glib-yaml-stream.c',
	'glib-yaml-document.c',
	'glib-yaml-node.c',
	'glib-yaml-alias-node.c',
	'glib-yaml-scalar-node.c',
	'glib-yaml-sequence-node.c',
	'glib-yaml-mapping-node.c',
)

deps = [
  gobject_introspection_dep,
  yaml_dep,
]

revision = 0
current = 1
age = 0
current_minus_age = current - age
project_libversion = '@0@.@1@.@2@'.format(current_minus_age, age, revision)

libglib_yaml = shared_library(
  '@0@-@1@'.format(project_name, major_version),
  version: project_libversion,
  sources: sources + headers,
  dependencies: deps,
  install: true,
)

libglib_yaml_dep = declare_dependency(
  dependencies: deps,
  link_with: libglib_yaml,
)

glib_yaml_libname = '@0@-@1@'.format(project_name, project_version)

pkg = import('pkgconfig')

pkg.generate(
  libglib_yaml,
  filebase: glib_yaml_libname,
  name: 'glib-yaml',
  description: 'YAML parser library',
  subdirs: 'lib' + glib_yaml_libname,
  requires: deps,
)

gnome = import('gnome')

# GObject Introspection
enable_introspection = get_option('introspection')
if enable_introspection
  gnome.generate_gir(
    libglib_yaml,
    sources: sources + headers,
    includes: 'Gtk-3.0',
    nsversion: project_version,
    namespace: 'Yaml',
    identifier_prefix: 'Yaml',
    symbol_prefix: project_name,
    export_packages: glib_yaml_libname,
    header: 'glib-yaml.h',
    install: true,
  )
endif
