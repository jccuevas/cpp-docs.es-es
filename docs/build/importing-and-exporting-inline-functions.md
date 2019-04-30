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
ms.openlocfilehash: ed523d84228124d4a8d99e443c0c744f362f1c56
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273448"
---
# <a name="importing-and-exporting-inline-functions"></a>Importar y exportar funciones inline

Las funciones importadas pueden definirse como en línea. El efecto es aproximadamente igual que definir una función estándar inline; las llamadas a la función se expanden en el código en línea, como una macro. Esto es especialmente útil como una forma de admitir C++ las clases en un archivo DLL directamente es posible que algunas de su funciones miembro para mejorar la eficacia.

Una característica de una función inline importada es que puede tomar su dirección en C++. El compilador devuelve la dirección de la copia de la función insertada que se encuentran en el archivo DLL. Otra característica de funciones insertadas importadas es que puede inicializar datos locales estáticos de la función importada, a diferencia de los datos importados globales.

> [!CAUTION]
>  Debe tener cuidado al proporcionar funciones inline importadas porque puede crear la posibilidad de conflictos de versión. Una función insertada se expande para crear el código de aplicación; por lo tanto, si más adelante vuelve a escribir la función, no se actualiza a menos que se vuelve a compilar la aplicación en Sí. (Normalmente, las funciones DLL se pueden actualizar sin volver a generar las aplicaciones que los usan.)

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportar desde un archivo DLL](exporting-from-a-dll.md)

- [Exportar desde un archivo DLL mediante. DEF (archivos)](exporting-from-a-dll-using-def-files.md)

- [Exportar desde un archivo DLL mediante__declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportar e importar utilizando AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Determinar qué método de exportación para usar](determining-which-exporting-method-to-use.md)

- [Importación a una aplicación mediante __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>Vea también

[Importar y exportar](importing-and-exporting.md)
