---
title: "Importar datos mediante __declspec(dllimport) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "dllimport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec(dllimport) (palabra clave) [C++]"
  - "dllimport (atributo) [C++], importaciones de datos"
  - "importar datos [C++]"
  - "importar archivos DLL [C++], __declspec(dllimport)"
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Importar datos mediante __declspec(dllimport)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el caso de los datos, es conveniente utilizar **\_\_declspec\(dllimport\)** para quitar un nivel de direccionamiento indirecto.  Cuando importe datos desde un archivo DLL, aún tendrá que recorrer la tabla de direcciones de importación.  Antes de que existiera **\_\_declspec\(dllimport\)**, esto significaba que tenía que acordarse de realizar un nivel de direccionamiento indirecto adicional al obtener acceso a datos exportados desde el archivo DLL:  
  
```  
// project.h  
#ifdef _DLL   // If accessing the data from inside the DLL  
   ULONG ulDataInDll;  
  
#else         // If accessing the data from outside the DLL  
   ULONG *ulDataInDll;  
#endif  
```  
  
 A continuación, se exportarían los datos del archivo .DEF:  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   CONSTANT  
```  
  
 y tendría acceso a los mismos fuera del archivo DLL:  
  
```  
if (*ulDataInDll == 0L)   
{  
   // Do stuff here  
}  
```  
  
 Ahora, cuando marca los datos como **\_\_declspec\(dllimport\)**, el compilador genera automáticamente el código de direccionamiento indirecto.  Ya no se tiene que preocupar de realizar los pasos anteriores.  Como se indicó anteriormente, no debe utilizar la declaración **\_\_declspec\(dllimport\)** en los datos al compilar el archivo DLL.  Las funciones del archivo DLL no utilizan la tabla de direcciones de importación para obtener acceso al objeto de datos; por lo tanto, no estará presente el nivel adicional de direccionamiento indirecto.  
  
 Para exportar los datos automáticamente desde el archivo DLL, utilice la siguiente dirección:  
  
```  
__declspec(dllexport) ULONG ulDataInDLL;  
```  
  
## Vea también  
 [Importar a una aplicación](../build/importing-into-an-application.md)