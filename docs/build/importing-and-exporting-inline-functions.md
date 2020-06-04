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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328512"
---
# <a name="importing-and-exporting-inline-functions"></a>Importar y exportar funciones inline

Las funciones importadas se pueden definir como insertadas. El efecto es aproximadamente el mismo que si se define una función estándar insertada; las llamadas a la función se expanden en código en línea, de forma muy parecida a una macro. Esto es útil sobre todo como una forma de admitir clases de C++ en un archivo DLL que podría alinear algunas de sus funciones miembro para mejorar la eficacia.

Una característica de una función insertada importada es que puede tomar su dirección en C++. El compilador devuelve la dirección de la copia de la función insertada que reside en el archivo DLL. Otra característica de las funciones insertadas importadas es que se pueden inicializar datos locales estáticos de la función importada, a diferencia de los datos importados globales.

> [!CAUTION]
> Debe tener cuidado al proporcionar funciones insertadas importadas, ya que pueden crear conflictos de versiones. Una función insertada se expande en el código de la aplicación; por tanto, si después vuelve a escribir la función, no se actualiza a menos que se vuelva a compilar la propia aplicación. (Normalmente, las funciones de DLL se pueden actualizar sin volver a generar las aplicaciones que las usan).

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportación desde un archivo DLL](exporting-from-a-dll.md)

- [Exportación desde un archivo DLL mediante archivos .DEF](exporting-from-a-dll-using-def-files.md)

- [Exportación desde un archivo DLL mediante __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportación e importación mediante AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportación de funciones de C++ para usarlas en ejecutables del lenguaje C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Determinación del método de exportación que se va a usar](determining-which-exporting-method-to-use.md)

- [Importación a una aplicación mediante __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>Vea también

[Importar y exportar](importing-and-exporting.md)
