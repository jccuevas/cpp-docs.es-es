---
title: "Determinar qué método de exportación que se utilizan | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- exporting DLLs [C++], method comparison
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7375d4baf31c1564493fd29938ef2ac8ee034f3e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="determining-which-exporting-method-to-use"></a>Determinar el método de exportación que se debe utilizar
Puede exportar funciones de dos maneras: un archivo .def o `__declspec(dllexport)` palabra clave. Para ayudarle a decidir qué forma es mejor para el archivo DLL, tenga en cuenta estas preguntas:  
  
-   ¿Tiene pensado exportar funciones más más tarde?  
  
-   ¿Es el archivo DLL utilizado sólo por aplicaciones que puede volver a generar o se usan las aplicaciones que no se puede volver a generar, por ejemplo, las aplicaciones que se crean por parte de terceros?  
  
## <a name="pros-and-cons-of-using-def-files"></a>Ventajas y desventajas del uso de archivos .def  
 Exportar funciones en un archivo .def permite controlar los ordinales de exportación. Cuando se agrega una función exportada en el archivo DLL, se puede asignar un valor ordinal mayor que cualquier otra función exportada. Al hacer esto, las aplicaciones que utilizan la vinculación implícita no tiene que volver a vincular con la biblioteca de importación que contiene la nueva función. Esto resulta muy útil si está diseñando un archivo DLL para usarlo muchas aplicaciones, ya que puede agregar nuevas funcionalidades y asegurarse también de que sigue funcionar correctamente con las aplicaciones que ya se basan en ella. Por ejemplo, los archivos DLL de MFC se generan utilizando .def (archivos).  
  
 Otra ventaja de utilizar un archivo .def es que puede usar el `NONAME` atributo para exportar una función. Esto coloca únicamente el ordinal de la tabla de exportaciones del archivo DLL. Archivos DLL que tiene un gran número de funciones exportadas, usando la `NONAME` atributo puede reducir el tamaño del archivo DLL. Para obtener información sobre cómo escribir una instrucción de definición de módulo, consulte [reglas para instrucciones de definición de módulo de](../build/reference/rules-for-module-definition-statements.md). Para obtener información acerca de la exportación de ordinales, vea [exportar funciones desde un archivo DLL por Ordinal en lugar de por nombre](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).  
  
 Una desventaja de utilizar un archivo .def es que si va a exportar funciones en un archivo de C++, tiene que colocar los nombres representativos en el .def archivo o definir las funciones exportadas mediante el uso de extern "C" para evitar la decoración de nombres que se lleva a cabo por el compilador de Visual C++.  
  
 Si coloca los nombres representativos en el archivo .def, se puede obtener mediante la [DUMPBIN](../build/reference/dumpbin-reference.md) de herramientas o mediante el vinculador [/MAP](../build/reference/map-generate-mapfile.md) opción. Los nombres representativos producidos por el compilador son específicos del compilador; por lo tanto, si coloca los nombres representativos producidos por el compilador en un archivo .def, las aplicaciones que se vinculan al archivo DLL también deberán generarse utilizando la misma versión del compilador para que los nombres representativos de la aplicación que realiza la llamada coincide con el nombre i n el archivo .def del archivo DLL.  
  
## <a name="pros-and-cons-of-using-declspecdllexport"></a>Ventajas y desventajas del uso de __declspec (dllexport)  
 Usar `__declspec(dllexport)` resulta práctico porque no tiene que preocuparse sobre cómo mantener un archivo .def y obtener los nombres representativos de las funciones exportadas. Sin embargo, la utilidad de esta forma de exportar está limitada por el número de aplicaciones vinculados que desea volver a generar. Si se vuelve a generar el archivo DLL con nuevas exportaciones, también deben generar las aplicaciones, ya que los nombres representativos para las funciones de C++ exportadas podrían cambiar si usa una versión diferente del compilador para volver a compilarlo.  
  
### <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?  
  
-   [Exportar desde un archivo DLL mediante archivos. DEF (archivos)](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar desde un archivo DLL mediante__declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exportar e importar utilizando AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Exportar funciones de C para utilizarlas en ejecutables de C o C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Importar a una aplicación mediante __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicializar un archivo DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Importar y exportar funciones inline](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importaciones mutuas](../build/mutual-imports.md)  
  
-   [Nombres representativos](../build/reference/decorated-names.md)  
  
## <a name="see-also"></a>Vea también  
 [Exportación desde un archivo DLL](../build/exporting-from-a-dll.md)