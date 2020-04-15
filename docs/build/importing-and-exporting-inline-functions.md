---
title: Importar y exportar funciones inline
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], inline functions
- inline functions [C++], importing
- DLLs [C++], importing
- importing functions [C++]
- DLLs [C++], exporting from
- importing inline functions [C++]
- inline functions [C++], exporting
- functions [C++], importing
- functions [C++], exporting
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
ms.openlocfilehash: abb0443ab8fbd315524350caaff34e0250147ed2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328512"
---
# <a name="importing-and-exporting-inline-functions"></a>Importar y exportar funciones inline

Las funciones importadas se pueden definir como en línea. El efecto es más o menos el mismo que definir una función estándar en línea; las llamadas a la función se expanden en código en línea, al igual que una macro. Esto es principalmente útil como una forma de admitir clases C++ en un archivo DLL que podría enlinear algunas de sus funciones miembro para la eficiencia.

Una característica de una función en línea importada es que puede tomar su dirección en C++. El compilador devuelve la dirección de la copia de la función en línea que reside en el archivo DLL. Otra característica de las funciones en línea importadas es que puede inicializar datos locales estáticos de la función importada, a diferencia de los datos importados globales.

> [!CAUTION]
> Debe tener cuidado al proporcionar funciones en línea importadas porque pueden crear la posibilidad de conflictos de versión. Una función en línea se expande en el código de la aplicación; por lo tanto, si más adelante vuelve a escribir la función, no se actualiza a menos que se vuelva a compilar la propia aplicación. (Normalmente, las funciones DLL se pueden actualizar sin volver a generar las aplicaciones que las utilizan.)

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportar de un archivo DLL](exporting-from-a-dll.md)

- [Exportar desde un archivo DLL mediante . Archivos DEF](exporting-from-a-dll-using-def-files.md)

- [Exportar desde un archivo DLL mediante__declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportar e importar utilizando AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Determinar qué método de exportación utilizar](determining-which-exporting-method-to-use.md)

- [Importación a una aplicación mediante __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>Consulte también

[Importar y exportar](importing-and-exporting.md)
