---
title: Exportar funciones desde un archivo DLL por ordinal en lugar de por nombre
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: 66e99b18d181e9067e90398c35a61db2da66c301
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328573"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Exportar funciones desde un archivo DLL por ordinal en lugar de por nombre

La forma más sencilla de exportar funciones desde el archivo DLL es exportarlas por nombre. Esto es lo que sucede cuando se utiliza **__declspec(dllexport),** por ejemplo. Pero en su lugar puede exportar funciones por ordinal. Con esta técnica, debe utilizar un archivo .def en lugar de **__declspec(dllexport).** Para especificar el valor ordinal de una función, anexe su ordinal al nombre de la función en el archivo .def. Para obtener información sobre cómo especificar ordinales, vea [Exportar desde un archivo DLL mediante archivos .def](exporting-from-a-dll-using-def-files.md).

> [!TIP]
> Si desea optimizar el tamaño de archivo del archivo DLL, utilice el atributo **NONAME** en cada función exportada. Con el atributo **NONAME,** los ordinales se almacenan en la tabla de exportación del archivo DLL en lugar de los nombres de función. Esto puede ser un ahorro considerable si está exportando muchas funciones.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Utilice un archivo .def para que pueda exportar por ordinal](exporting-from-a-dll-using-def-files.md)

- [Usar __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>Consulte también

[Exportar desde un archivo DLL](exporting-from-a-dll.md)
