---
title: "Determinar el m&#233;todo de exportaci&#243;n que se debe utilizar | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".def (archivos) [C++], exportar desde DLL"
  - "__declspec(dllexport) (palabra clave) [C++]"
  - "def (archivos) [C++], exportar desde DLL"
  - "exportar DLL [C++], comparación de métodos"
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Determinar el m&#233;todo de exportaci&#243;n que se debe utilizar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede exportar funciones en dos del archivo de las maneras \- uno .def o palabra clave de `__declspec(dllexport)` .  Para ayudarle a decidir qué es mejor para el archivo DLL, considere estas preguntas:  
  
-   ¿Pretende exportar más funciones más adelante?  
  
-   ¿DLL sólo se utiliza en las aplicaciones que puede recompilar, o bien usan las aplicaciones que no puede recompilar\- para el ejemplo, las aplicaciones creadas por terceros?  
  
## Ventajas y desventajas de utilizar archivos .def  
 Exportar funciones de un archivo .def permite controlar sobre los ordinales de exportación.  Al agregar una función exportada a la DLL, puede asignar un valor ordinal más alto que cualquier otra función exportada.  Cuando lo haga, las aplicaciones que utilizan la vinculación implícita no tienen que volver a vincularse a la biblioteca de importación que contiene la nueva función.  Esto es muy útil si está diseñando un archivo DLL para uso de muchas aplicaciones porque puede agregar nueva funcionalidad y asegurarse también de que continúa funcionando correctamente con aplicaciones que confían ya en ella.  Por ejemplo, los archivos DLL de MFC se compilan utilizando archivos .def.  
  
 Otra ventaja de utilizar un archivo .def es que puede utilizar el atributo de `NONAME` exportar una función.  Esto sólo coloca el ordinal en la tabla de exportaciones de DLL.  Para los archivos DLL con un gran número de funciones exportadas, mediante el atributo de `NONAME` puede reducir el tamaño del archivo DLL.  Para obtener información sobre cómo escribir una instrucción de definición de módulo, vea [Reglas para instrucciones de definición de módulos](../build/reference/rules-for-module-definition-statements.md).  Para obtener información acerca de la exportación ordinal, vea [Exportar funciones desde un archivo DLL por ordinal en lugar de por nombre](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).  
  
 Una desventaja de utilizar un archivo .def es que si exporta funciones de un archivo de c\+\+., tiene que colocar los nombres representativos en el archivo .def o definir las funciones exportadas mediante extern “C” para evitar la decoración de nombres que es realizada por el compilador de Visual C\+\+.  
  
 Si coloca los nombres representativos en el archivo .def, puede obtenerlos mediante la herramienta de [DUMPBIN](../build/reference/dumpbin-reference.md) o con la opción de [\/MAP](../build/reference/map-generate-mapfile.md) del vinculador.  Los nombres representativos generados por el compilador son compilador\- específicos; por consiguiente, si coloca los nombres representativos generados por el compilador en un archivo .def, también deberán generarse las aplicaciones que se vinculan al archivo DLL mediante la misma versión del compilador para los nombres representativos en la coincidencia de la aplicación que realiza la llamada los nombres exportados en el archivo .def del archivo DLL.  
  
## Ventajas y desventajas de utilizar \_\_declspec\(dllexport\)  
 Mediante `__declspec(dllexport)` es conveniente porque no tiene que preocuparse de mantener un archivo .def y obtener los nombres representativos de las funciones exportadas.  Sin embargo, la utilidad de esta manera de exportar está limitada por número de aplicaciones vinculadas que está dispuesto recompilar.  Si recompila el archivo DLL con nuevas exportaciones, también tiene que recompilar las aplicaciones porque los nombres representativos de las funciones de C\+\+ exportadas podrían cambiar si utiliza una versión diferente del compilador para recompilarlo.  
  
### ¿Qué desea hacer?  
  
-   [Exportar desde un archivo DLL mediante archivos .DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar desde un archivo DLL mediante \_\_declspec\(dllexport\)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exportar e importar utilizando AFX\_EXT\_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exportar funciones de C\+\+ para utilizarlas en ejecutables en lenguaje C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Exportar funciones de C para utilizarlas en ejecutables en lenguaje C o C\+\+](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Importar a una aplicación mediante \_\_declspec\(dllimport\)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicializar un archivo DLL](../build/initializing-a-dll.md)  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Importar y exportar funciones inline](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importaciones mutuas](../build/mutual-imports.md)  
  
-   [Nombres representativos](../build/reference/decorated-names.md)  
  
## Vea también  
 [Exportar desde un archivo DLL](../build/exporting-from-a-dll.md)