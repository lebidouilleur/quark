# meson.build ---                                            -*- mode: meson; -*-
#
# Copyright (C) 2021  lebidouilleur
#
# Author: lebidouilleur <lebidouilleur@icloud.com>
# Keywords:
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#
# Code:
#




# Project definition.
project(                 'QUARK',
                         'c',
                license: 'GPL3+',
                version: '0.0.1',
          meson_version: '>= 0.55.0',
        default_options: [ 'c_std=c17',      'cpp_std=c++17',
                           'optimization=3', 'warning_level=3' ])





# Define the language used for the project.
# Default is 'c'.  You can choose between [c,cpp,...].
LANGUAGE = 'c'






prefix     = get_option('prefix')
bindir     = join_paths(prefix, get_option('bindir'))
libdir     = join_paths(prefix, get_option('libdir'))
mandir     = join_paths(prefix, get_option('mandir'))
datadir    = join_paths(prefix, get_option('datadir'))
localedir  = get_option('localedir')






# Setup the compiler
cc = meson.get_compiler(LANGUAGE)
if  get_option('buildtype') == 'release'
  compile_flags = [ '-march=native', '-mtune=native', '-pipe' ]

  supported_flags = cc.get_supported_arguments(compile_flags)
  add_project_arguments(supported_flags, language: LANGUAGE)
else
  if get_option('buildtype').startswith('debug')
    # Add compilation flags
    compile_flags = [ '-W',
                      '-Wdeclaration-after-statement',
                      '-Wcast-align',
                      '-Wcast-qual',
                      '-Wconversion',
                      '-Werror',
                      '-Werror=address',
                      '-Werror=array-bounds',
                      '-Werror=empty-body',
                      '-Werror=implicit',
                      '-Werror=implicit-function-declaration',
                      '-Werror=incompatible-pointer-types',
                      '-Werror=init-self',
                      '-Werror=int-conversion',
                      '-Werror=int-to-pointer-cast',
                      '-Werror=main',
                      '-Werror=misleading-indentation',
                      '-Werror=missing-braces',
                      '-Werror=missing-include-dirs',
                      '-Werror=nonnull',
                      '-Werror=overflow',
                      '-Werror=parenthesis',
                      '-Werror=pointer-arith',
                      '-Werror=pointer-to-int-cast',
                      '-Werror=redundant-decls',
                      '-Werror=return-type',
                      '-Werror=sequence-point',
                      '-Werror=shadow',
                      '-Werror=strict-prototypes',
                      '-Werror=trigraphs',
                      '-Werror=undef',
                      '-Werror=write-strings',
                      '-Wformat-nonliteral',
                      '-Wignored-qualifiers',
                      '-Wimplicit-function-declaration',
                      '-Wlogical-op',
                      '-Wmissing-declarations',
                      '-Wmissing-format-attribute',
                      '-Wmissing-include-dirs',
                      '-Wmissing-noreturn',
                      '-Wmissing-prototype',
                      '-Wnested-externs',
                      '-Wno-cast-function-type',
                      '-Wno-missing-field-initializers',
                      '-Wno-sign-compare',
                      '-Wno-unused-parameter',
                      '-Wold-style-definition',
                      '-Wpointer-arith',
                      '-Wredundant-decls',
                      '-Wshadow',
                      '-Wstrict-prototypes',
                      '-Wswitch-default',
                      '-Wswitch-enum',
                      '-Wundef',
                      '-Wuninitialized',
                      '-Wunused',
                      '-Wwrite-strings',
                      '-fno-strict-aliasing',
                      ['-Werror=format-security', '-Werror=format=2' ],
                      '-g' ]

    supported_flags = cc.get_supported_arguments(compile_flags)
    add_project_arguments(supported_flags, language: LANGUAGE)
  endif
endif

includeDir = include_directories('include')

executable('quark', 'main.c', include_directories: includeDir,
                              install: true)
