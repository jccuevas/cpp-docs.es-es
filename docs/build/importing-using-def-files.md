---
title: "Importar mediante archivos DEF | Microsoft Docs"
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
  - ".def (archivos) [C++], importar con"
  - "def (archivos) [C++], importar con"
  - "dllimport (atributo) [C++], DEF (archivos)"
  - "DLL [C++], DEF (archivos)"
  - "importar archivos DLL [C++], DEF (archivos)"
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Importar mediante archivos DEF
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si decide utilizar **\_\_declspec\(dllimport\)** junto con un archivo .def, deberá cambiar el archivo .def para que utilice DATA en lugar de CONSTANT, a fin de reducir la posibilidad de que haya errores de código que den problemas:  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   DATA  
```  
  
 En la tabla siguiente se muestra la causa.  
  
|Palabra clave|Se genera en la biblioteca de importación|Exporta|  
|-------------------|-----------------------------------------------|-------------|  
|`CONSTANT`|`_imp_ulDataInDll_ulDataInDll`|`_ulDataInDll`|  
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|  
  
 Si utiliza **\_\_declspec\(dllimport\)** y CONSTANT, se mostrarán la versión de `imp` y el nombre no representativo de la biblioteca de importación .lib del archivo DLL que se crea para permitir la vinculación explícita.  Si utiliza **\_\_declspec\(dllimport\)** y DATA, sólo se mostrará la versión de `imp` del nombre.  
  
 Si utiliza CONSTANT, cualquiera de las siguientes construcciones de código son válidas para tener acceso a `ulDataInDll`:  
  
```  
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 O bien  
  
```  
ULONG *ulDataInDll;      /*prototype*/  
if (*ulDataInDll == 0L)  /*sample code fragment*/  
```  
  
 Sin embargo, si utiliza DATA en el archivo .def, sólo el código compilado con la siguiente definición tendrá acceso a la variable `ulDataInDll`:  
  
```  
__declspec(dllimport) ULONG ulDataInDll;  
  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 El uso de CONSTANT es más arriesgado porque si olvida utilizar el nivel adicional de direccionamiento indirecto, podría tener acceso al puntero de la tabla de direcciones de importación a la variable, pero no a la variable misma.  Este tipo de problema puede manifestarse como una infracción de acceso porque el compilador y el vinculador conviertan actualmente la tabla de direcciones de importación en una tabla de sólo lectura.  
  
 El vinculador actual de Visual C\+\+ emite una advertencia si el archivo .def incluye CONSTANT para tenerlo en cuenta.  La única razón para utilizar CONSTANT es que no se haya podido volver a compilar un archivo objeto en el que el archivo de encabezado no mostrara **\_\_declspec\(dllimport\)** en el prototipo.  
  
## Vea también  
 [Importar a una aplicación](../build/importing-into-an-application.md)