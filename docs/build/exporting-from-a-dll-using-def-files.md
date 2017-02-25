---
title: "Exportar desde un archivo DLL mediante archivos DEF | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "def (archivos) [C++], exportar desde DLL"
  - "exportar DLL [C++], DEF (archivos)"
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Exportar desde un archivo DLL mediante archivos DEF
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un archivo de definición de módulo \(.def\) es un archivo de texto que contiene una o varias instrucciones de módulo que describen distintos atributos de un archivo DLL.  Si no utiliza la palabra clave **\_\_declspec\(dllexport\)** para exportar las funciones del archivo DLL, el archivo DLL requerirá un archivo .def.  
  
 Un archivo .def mínimo debe contener las siguientes instrucciones de definición de módulo:  
  
-   La primera instrucción del archivo debe ser la instrucción LIBRARY.  Esta instrucción identifica el archivo .def como perteneciente a un archivo DLL.  A la instrucción LIBRARY le sigue el nombre del archivo DLL.  El vinculador coloca este nombre en la biblioteca de importación del archivo DLL.  
  
-   La instrucción EXPORTS muestra los nombres y, opcionalmente, los valores ordinales de las funciones exportadas por el archivo DLL.  Para asignar a la función un valor ordinal debe escribir a continuación del nombre de la función el signo @ \(arroba\) y un número.  Cuando especifique valores ordinales, deberán estar dentro del intervalo de 1 a N, donde N es el número de funciones exportadas por el archivo DLL.  Si desea exportar funciones por ordinal, vea [Exportar funciones desde un archivo DLL por ordinal en lugar de por nombre](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md), así como este tema.  
  
 Por ejemplo, un archivo DLL que contiene el código para implementar un árbol de búsqueda binaria podría tener la siguiente apariencia:  
  
```  
LIBRARY   BTREE  
EXPORTS  
   Insert   @1  
   Delete   @2  
   Member   @3  
   Min   @4  
```  
  
 Si utiliza el [Asistente para archivos DLL de MFC](../mfc/reference/mfc-dll-wizard.md) para crear un archivo DLL de MFC, el asistente creará un archivo .def de estructura y lo agregará automáticamente al proyecto.  Agregue a este archivo los nombres de las funciones que se van a exportar.  Para archivos DLL que no estén basados en MFC, deberá crear personalmente el archivo .def y agregarlo al proyecto.  
  
 Si va a exportar funciones de un archivo de C\+\+, tendrá que colocar los nombres representativos en el archivo .def o definir las funciones exportadas con vinculación C estándar utilizando extern "C".  Si tiene que colocar los nombres representativos en el archivo .def, puede obtenerlos mediante la herramienta [DUMPBIN](../build/reference/dumpbin-reference.md) o con la opción [\/MAP](../build/reference/map-generate-mapfile.md) del vinculador.  Tenga en cuenta que los nombres representativos producidos por el compilador serán específicos del compilador.  Si coloca los nombres representativos producidos por el compilador de Visual C\+\+ en un archivo .def, las aplicaciones que se vinculan al archivo DLL también deben generarse con la misma versión de Visual C\+\+, de forma que los nombres representativos de la aplicación que hace la llamada coincidan con los nombres exportados del archivo .def del archivo DLL.  
  
 Si está compilando un [archivo DLL de extensión](../build/extension-dlls-overview.md) y exportando mediante un archivo .def, coloque el código siguiente al principio y al final de los archivos de encabezado que contienen las clases exportadas:  
  
```  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
 Estas líneas garantizan que se exportan \(o importan\) las variables MFC utilizadas internamente o agregadas a las clases desde el archivo DLL de extensión.  Por ejemplo, al derivar una clase mediante `DECLARE_DYNAMIC`, la macro se expandirá para agregar una variable miembro `CRuntimeClass` a la clase.  Si no incluye estas cuatro líneas, el archivo DLL puede compilarse o vincularse incorrectamente, o causar un error cuando se vincule la aplicación cliente al archivo DLL.  
  
 Al generar el archivo DLL, el vinculador utiliza el archivo .def para crear un archivo de exportación \(.exp\) y un archivo de biblioteca de importación \(.lib\).  El vinculador utiliza después el archivo de exportación para compilar el archivo DLL.  Los ejecutables que se vinculan implícitamente al archivo DLL se vinculan a la biblioteca de importación cuando se compilan.  
  
 Tenga en cuenta que MFC utiliza archivos .def para exportar funciones y clases desde MFCx0.dll.  
  
## ¿Qué desea hacer?  
  
-   [Exportar desde un archivo DLL mediante \_\_declspec\(dllexport\)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exportar e importar utilizando AFX\_EXT\_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exportar funciones de C\+\+ para utilizarlas en ejecutables en lenguaje C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Exportar funciones de C para utilizarlas en ejecutables en lenguaje C o C\+\+](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Determinar el método de exportación que se va a utilizar](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importar a una aplicación mediante \_\_declspec\(dllimport\)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicializar un archivo DLL](../build/initializing-a-dll.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [archivos .def](../build/reference/module-definition-dot-def-files.md)  
  
-   [Reglas para instrucciones de definición de módulos](../build/reference/rules-for-module-definition-statements.md)  
  
-   [Nombres representativos](../build/reference/decorated-names.md)  
  
-   [Importar y exportar funciones inline](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importaciones mutuas](../build/mutual-imports.md)  
  
## Vea también  
 [Exportar desde un archivo DLL](../build/exporting-from-a-dll.md)