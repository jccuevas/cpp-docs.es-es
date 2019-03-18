---
title: Exportar funciones desde un archivo DLL por ordinal en lugar de por nombre
ms.date: 11/04/2016
f1_keywords:
- NONAME
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: 26b9a51a440e4e05c39908cb437d82e2e08e30c9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812075"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Exportar funciones desde un archivo DLL por ordinal en lugar de por nombre

La manera más sencilla de exportar funciones desde el archivo DLL es exportarlas por nombre. Esto es lo que sucede cuando se usa **__declspec (dllexport)**, por ejemplo. Pero en su lugar, puede exportar funciones por ordinal. Con esta técnica, debe usar un archivo .def en lugar de **__declspec (dllexport)**. Para especificar el valor ordinal de la función, anexe el nombre de función en el archivo .def su ordinal. Para obtener información acerca de cómo especificar las posiciones ordinales, vea [exportar desde un archivo DLL mediante archivos .def](exporting-from-a-dll-using-def-files.md).

> [!TIP]
>  Si desea optimizar el tamaño del archivo DLL, utilice el **NONAME** atributo en cada función exportada. Con el **NONAME** atributo, los ordinales se almacenan en la DLL exporte la tabla en lugar de los nombres de función. Esto puede suponer un ahorro considerable si va a exportar muchas funciones.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Usar un archivo .def para exportar por ordinal](exporting-from-a-dll-using-def-files.md)

- [Use __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>Vea también

[Exportación desde un archivo DLL](exporting-from-a-dll.md)
