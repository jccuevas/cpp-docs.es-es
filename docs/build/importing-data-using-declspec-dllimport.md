---
title: Importar datos mediante __declspec (dllimport) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- dllimport
dev_langs:
- C++
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9877c5a229c3cabcb7703dd2617d1d57e3512f0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368517"
---
# <a name="importing-data-using-declspecdllimport"></a>Importar datos mediante __declspec(dllimport)
En el caso de los datos mediante **__declspec (dllimport)** es un elemento de conveniencia que quita una capa de direccionamiento indirecto. Al importar datos desde un archivo DLL, también tendrá que ir a través de la tabla de direcciones de importación. Antes de **__declspec (dllimport)**, esto significaba que tenía que acordarse de realizar un nivel adicional de direccionamiento indirecto al obtener acceso a datos exportados desde el archivo DLL:  
  
```  
// project.h  
#ifdef _DLL   // If accessing the data from inside the DLL  
   ULONG ulDataInDll;  
  
#else         // If accessing the data from outside the DLL  
   ULONG *ulDataInDll;  
#endif  
```  
  
 A continuación, exportaría los datos en el. Archivo DEF:  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   CONSTANT  
```  
  
 y tener acceso a él fuera del archivo DLL:  
  
```  
if (*ulDataInDll == 0L)   
{  
   // Do stuff here  
}  
```  
  
 Cuando marca los datos como **__declspec (dllimport)**, el compilador genera automáticamente el código de direccionamiento indirecto para usted. Ya no tiene que preocuparse de los pasos anteriores. Como se mencionó anteriormente, no use **__declspec (dllimport)** declaración en los datos al generar el archivo DLL. Funciones en el archivo DLL no utilizan la tabla de direcciones de importación para tener acceso al objeto de datos; por lo tanto, no tendrá el nivel adicional de direccionamiento indirecto.  
  
 Para exportar los datos automáticamente desde el archivo DLL, utilice esta declaración:  
  
```  
__declspec(dllexport) ULONG ulDataInDLL;  
```  
  
## <a name="see-also"></a>Vea también  
 [Importación a una aplicación](../build/importing-into-an-application.md)