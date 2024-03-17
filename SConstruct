import fnmatch
import os
import scons_compiledb

#Setup environment
file_match = "*.cpp"

#Recursive Glob method to find all source files
matches = []
for root, dirnames, filenames in os.walk("src/"):
    for filename in filenames:
        if fnmatch.fnmatch(filename, file_match):
            matches.append(os.path.join(root, filename))


env = Environment(CPPPATH = ['/opt/homebrew/Cellar/sfml/2.6.1/include/',
                             '/opt/homebrew/Cellar/glew/2.2.0_1/include/',
                             '/Users/playwright/Projects/cpp-tutorials/sfml-imgui/dependencies/imgui/',
                             ],
                             CXXFLAGS="-std=c++17"
);

matches.append(os.path.join('dependencies/imgui/imgui.cpp'))
matches.append(os.path.join('dependencies/imgui/imgui_widgets.cpp'))
matches.append(os.path.join('dependencies/imgui/imgui_draw.cpp'))
matches.append(os.path.join('dependencies/imgui/imgui_demo.cpp'))
matches.append(os.path.join('dependencies/imgui/imgui_tables.cpp'))
matches.append(os.path.join('dependencies/imgui/imgui-SFML.cpp'))


scons_compiledb.enable(env);

env['FRAMEWORKS']=['OpenGL']


env.Append(LIBPATH = ["/opt/homebrew/Cellar/sfml/2.6.1/lib",'/opt/homebrew/Cellar/glew/2.2.0_1/lib']);
env.Append(LIBS = ["sfml-graphics","sfml-window","sfml-system","GLEW"]);
env.Program(target = "Game", source = matches)


env.CompileDb();