project(
  'mate-pluma', 'c',
  version: '1.26.1',
  meson_version: '>=0.47.0',
  license: 'GPL2',
  default_options : [ 'warning_level=1', 'buildtype=debugoptimized', 'c_std=gnu11'],
)

package_name = meson.project_name()
package_version = meson.project_version()

# Versioning
version_arr = package_version.split('.')
version_major = version_arr[0].to_int()
version_minor = version_arr[1].to_int()
version_micro = version_arr[2].to_int()

package_string = '@0@ @1@.0'.format(package_name, package_version)

config_h = configuration_data()
config_h.set_quoted('PACKAGE', package_name, description: 'Name of package')
config_h.set_quoted('PACKAGE_NAME', package_name, description: 'Define to the full name of this package.')
config_h.set_quoted('PACKAGE_STRING', package_string, description: 'Define to the full name and version of this package.')
config_h.set_quoted('PACKAGE_VERSION', package_version, description: 'Define to the version of this package.')
config_h.set_quoted('PACKAGE_URL', 'https://mate-desktop.org', description: 'Define to the home page for this package.')
config_h.set_quoted('GETTEXT_PACKAGE', package_name, description: 'Gettext package')
config_h.set_quoted('VERSION', package_version, description: 'Name of package')

# Compiler & Project arguments
add_project_arguments([
  '-DHAVE_CONFIG_H',
  '-I' + meson.build_root(),
  ], language: 'c')



glib_req = '>= 2.50.0'
gio_req = '>= 2.50.0'
gtk_req = '>= 3.22.0'
dconf_req = '>= 0.13.4'
ice_req = '>= 1.0.0'
sm_req = '>= 1.0.0'

xml2_dep = dependency('libxml-2.0',)
glib_dep = dependency('glib-2.0', version: glib_req)
gtk_dep = dependency('gtk+-3.0', version: gtk_req)
gio_dep = dependency('gio-2.0', version: gio_req)
dconf_dep = dependency('dconf', version: dconf_req)
gtksourceview_dep = dependency('gtksourceview-4')
peas_dep = dependency('libpeas-gtk-1.0')
x11_dep = dependency('x11')

i18n = import('i18n')

term_deps = [
  x11_dep,
  xml2_dep,
  glib_dep,
  gio_dep,
  gtk_dep,
  dconf_dep,
  gtksourceview_dep,
  peas_dep
]

# Paths
rootdir = include_directories('.')

srcdir = meson.current_source_dir()
builddir = meson.current_build_dir()

prefix = get_option('prefix')

buildtype = get_option('buildtype')

bindir = join_paths(prefix, get_option('bindir'))
libdir = join_paths(prefix, get_option('libdir'))
datadir = join_paths(prefix, get_option('datadir'))
pkgdatadir = join_paths(datadir, package_name)

subdir('pluma/dialogs')

sm_dep = dependency('sm', version: sm_req, required: false)
build_sm = false
ice_dep = dependency('ice', version: ice_req, required: false)
if get_option('sm') and sm_dep.found() and ice_dep.found()
  build_sm = true
  config_h.set('HAVE_SMCLIENT', 1)
  mate_submodules_dep = dependency('mate-submodules', version: '1.24.0',
    fallback: ['mate-submodules', 'mate_submodules_dep'])
  term_deps += [mate_submodules_dep]
endif

configure_file(
  output: 'config.h',
  configuration: config_h
)
subdir('pluma')

