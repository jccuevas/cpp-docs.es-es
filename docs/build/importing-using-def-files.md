---
title: Importar mediante archivos DEF | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ee213f1aa381415444288dbab4473cae6f5fc7b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="importing-using-def-files"></a>Importar mediante archivos DEF
Si opta por usar **__declspec (dllimport)** junto con un archivo .def, debe cambiar el archivo .def para utilizar datos en lugar de constante para reducir la probabilidad de que la codificación incorrecta se producirá un problema:  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   DATA  
```  
  
 En la tabla siguiente se muestra por qué.  
  
|Palabra clave|Se genera en la biblioteca de importación|Exportaciones|  
|-------------|---------------------------------|-------------|  
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|  
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|  
  
 Usando **__declspec (dllimport)** y constante muestra tanto la `imp` versión y el nombre no representativo de la DLL de .lib importación biblioteca que se crea para permitir la vinculación explícita. Usar **__declspec (dllimport)** y listas de datos simplemente el `imp` versión del nombre.  
  
 Si utiliza CONSTANT, se puede utilizar cualquiera de las siguientes construcciones de código para tener acceso a `ulDataInDll`:  
  
```  
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 O bien  
  
```  
ULONG *ulDataInDll;      /*prototype*/  
if (*ulDataInDll == 0L)  /*sample code fragment*/  
```  
  
 Sin embargo, si usa datos en el archivo .def, sólo el código compilado con la siguiente definición puede tener acceso a la variable `ulDataInDll`:  
  
```  
__declspec(dllimport) ULONG ulDataInDll;  
  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 Uso constante es más arriesgado porque si olvida utilizar el nivel adicional de direccionamiento indirecto, podría tener acceso puntero de la tabla de direcciones de importación a la variable, no la propia variable. Este tipo de problema puede manifestarse como una infracción de acceso porque la tabla de direcciones de importación estará actualmente solo lectura mediante el compilador y el vinculador.  
  
 El vinculador actual de Visual C++ emite una advertencia si ve CONSTANT en el archivo .def para tener en cuenta este caso. La única razón para utilizar CONSTANT es si no se puede volver a compilar algún archivo objeto donde el archivo de encabezado no indica **__declspec (dllimport)** en el prototipo.  
  
## <a name="see-also"></a>Vea también  
 [Importación a una aplicación](../build/importing-into-an-application.md)
