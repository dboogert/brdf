cmake_minimum_required(VERSION 2.8)

project(brdf)

SET(QT_USE_QTOPENGL TRUE)

find_package(Qt4 REQUIRED)
find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)

#FIND_LIBRARY (PTEX_LIBRARY ptx)

if(NOT OPENGL_FOUND)
    message(ERROR " OPENGL not found!")
endif(NOT OPENGL_FOUND)

MESSAGE(STATUS "APPLE OSX")
set(EXTERNAL_LIBS glew FreeImage)
MESSAGE(STATUS GL=${OPENGL_INCLUDE_DIR})
MESSAGE(STATUS GLUT=${GLUT_INCLUDE_DIR})
include(${QT_USE_FILE})
add_definitions(${QT_DEFINITIONS})

include_directories(${OPENGL_INCLUDE_DIR} ${GLUT_INCLUDE_DIR} )

set(sources 	src/brdf/BRDFAnalytic.cpp
				src/brdf/BRDFBase.cpp
				src/brdf/BRDFImageSlice.cpp
				src/brdf/BRDFMeasuredAniso.cpp
				src/brdf/BRDFMeasuredMERL.cpp
				src/brdf/ColorVarWidget.cpp
				src/brdf/DGLFrameBuffer.cpp
				src/brdf/DGLShader.cpp
				src/brdf/FloatVarWidget.cpp
				src/brdf/IBLWidget.cpp
				src/brdf/IBLWindow.cpp
				src/brdf/ImageSliceWidget.cpp
				src/brdf/ImageSliceWindow.cpp
				src/brdf/LitSphereWidget.cpp
				src/brdf/LitSphereWindow.cpp
				src/brdf/MainWindow.cpp
				src/brdf/ParameterGroupWidget.cpp
				src/brdf/ParameterWindow.cpp
				src/brdf/Paths.cpp
				src/brdf/Plot3DWidget.cpp
				src/brdf/PlotCartesianWidget.cpp
				src/brdf/PlotCartesianWindow.cpp
				src/brdf/PlotPolarWidget.cpp
				src/brdf/SharedContextGLWidget.cpp
				src/brdf/ShowingDockWidget.cpp
				src/brdf/SimpleModel.cpp
				src/brdf/main.cpp
				src/brdf/ptex/PtexCache.cpp
				src/brdf/ptex/PtexHalf.cpp
				src/brdf/ptex/PtexReader.cpp
				src/brdf/ptex/PtexUtils.cpp
)

set(headers		src/brdf/BRDFAnalytic.h
				src/brdf/BRDFBase.h
				src/brdf/BRDFImageSlice.h
				src/brdf/BRDFMeasuredAniso.h
				src/brdf/BRDFMeasuredMERL.h
				src/brdf/ColorVarWidget.h
				src/brdf/DGLFrameBuffer.h
				src/brdf/DGLShader.h
				src/brdf/FloatVarWidget.h
				src/brdf/IBLWidget.h
				src/brdf/IBLWindow.h
				src/brdf/ImageSliceWidget.h
				src/brdf/ImageSliceWindow.h
				src/brdf/LitSphereWidget.h
				src/brdf/LitSphereWindow.h
				src/brdf/MainWindow.h
				src/brdf/ParameterGroupWidget.h
				src/brdf/ParameterWindow.h
				src/brdf/Paths.h
				src/brdf/Plot3DWidget.h
				src/brdf/PlotCartesianWidget.h
				src/brdf/PlotCartesianWindow.h
				src/brdf/PlotPolarWidget.h
				src/brdf/SharedContextGLWidget.h
				src/brdf/ShowingBase.h
				src/brdf/ShowingDockWidget.h
				src/brdf/SimpleModel.h
				src/brdf/angleConvert.h
				src/brdf/bitmapContainer.h
				src/brdf/geodesicHemisphere.h
				src/brdf/trim.h
)

QT4_WRAP_CPP(headers_moc ${headers})

add_executable(brdf ${headers_moc} ${sources} ${headers})
target_link_libraries(brdf ${QT_LIBRARIES} ${OPENGL_LIBRARY} ${EXTERNAL_LIBS})