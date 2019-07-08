project ('volk', 'c',
         default_options : ['werror=true',
                            'warning_level=2'])

# source files
volk_headers = ['volk.h']

volk_sources = ['volk.c']

# if VULKAN_SDK is defined type_name is 'vulkan_sdk'
# and we want its include directories only
vulkan_dep = dependency ('vulkan')

deps = []
if (vulkan_dep.type_name () == 'vulkan_sdk')
  deps += vulkan_dep.partial_dependencies (includes : true)
endif

# dl is a bit weird in meson
cc = meson.get_compiler('c')
dl_dep = cc.find_library('dl', required : false)
deps += dl_dep

inc = include_directories('.')

volk_lib = static_library ('volk', volk_sources,
                           include_directories : inc,
                           dependencies : deps,
                           install : true)

volk_dep = declare_dependency (include_directories : inc,
                               dependencies : deps,
                               link_with : volk_lib)

