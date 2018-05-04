---
title: Exportar funciones desde un archivo DLL por Ordinal en lugar de por nombre | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- NONAME
dev_langs:
- C++
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b05f3e429406b3c24c7a21ce9ee8e10fe19c14b8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Exportar funciones desde un archivo DLL por ordinal en lugar de por nombre
La manera más sencilla de exportar funciones desde el archivo DLL es exportarlas por nombre. Esto es lo que ocurre cuando se usa **__declspec (dllexport)**, por ejemplo. Pero en su lugar, puede exportar funciones por ordinal. Con esta técnica, debe utilizar un archivo .def en lugar de **__declspec (dllexport)**. Para especificar el valor ordinal de la función, anexe su ordinal al nombre de función en el archivo .def. Para obtener información acerca de cómo especificar ordinales, vea [exportar desde un archivo DLL mediante archivos .def](../build/exporting-from-a-dll-using-def-files.md).  
  
> [!TIP]
>  Si desea optimizar el tamaño del archivo DLL, utilice la **NONAME** atributo en cada función exportada. Con el **NONAME** atributo, los ordinales se almacenan en la DLL exporte la tabla en lugar de los nombres de función. Esto puede ser un ahorro considerable si va a exportar muchas funciones.  
  
## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?  
  
-   [Utilizar un archivo .def para exportar por ordinal](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Utilizar __declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
## <a name="see-also"></a>Vea también  
 [Exportación desde un archivo DLL](../build/exporting-from-a-dll.md)