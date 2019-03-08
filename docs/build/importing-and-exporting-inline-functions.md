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
ms.openlocfilehash: fb117ce6c6088b9fdca57f7d4fd7d0193e1813c2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425554"
---
# <a name="importing-and-exporting-inline-functions"></a>Importar y exportar funciones inline

Las funciones importadas pueden definirse como en línea. El efecto es aproximadamente igual que definir una función estándar inline; las llamadas a la función se expanden en el código en línea, como una macro. Esto es especialmente útil como una forma de admitir C++ las clases en un archivo DLL directamente es posible que algunas de su funciones miembro para mejorar la eficacia.

Una característica de una función inline importada es que puede tomar su dirección en C++. El compilador devuelve la dirección de la copia de la función insertada que se encuentran en el archivo DLL. Otra característica de funciones insertadas importadas es que puede inicializar datos locales estáticos de la función importada, a diferencia de los datos importados globales.

> [!CAUTION]
>  Debe tener cuidado al proporcionar funciones inline importadas porque puede crear la posibilidad de conflictos de versión. Una función insertada se expande para crear el código de aplicación; por lo tanto, si más adelante vuelve a escribir la función, no se actualiza a menos que se vuelve a compilar la aplicación en Sí. (Normalmente, las funciones DLL se pueden actualizar sin volver a generar las aplicaciones que los usan.)

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportar desde un archivo DLL](../build/exporting-from-a-dll.md)

- [Exportar desde un archivo DLL mediante. DEF (archivos)](../build/exporting-from-a-dll-using-def-files.md)

- [Exportar desde un archivo DLL mediante__declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportar e importar utilizando AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Determinar qué método de exportación para usar](../build/determining-which-exporting-method-to-use.md)

- [Importar a una aplicación mediante __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>Vea también

[Importar y exportar](../build/importing-and-exporting.md)
