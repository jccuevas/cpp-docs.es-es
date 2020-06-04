---
title: Administración de memoria con CStringT
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, memory management
- memory [C++], usage
- IAtlStringMgr class, using
- strings [C++], custom memory management
- CFixedStringT class, description of
- strings [C++], memory management
- CStringT class, memory management
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
ms.openlocfilehash: af042c80b9e3e0de872261f89255a26728b218cd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440507"
---
# <a name="memory-management-with-cstringt"></a>Administración de memoria con CStringT

La clase [CStringT](../atl-mfc-shared/reference/cstringt-class.md) es una clase de plantilla que se utiliza para manipular cadenas de caracteres de longitud variable. La memoria para contener estas cadenas se asigna y libera a través de un objeto de administrador de cadenas, asociado a cada instancia de `CStringT`. MFC y ATL proporcionan instancias predeterminadas de `CStringT`, denominadas `CString`, `CStringA`y `CStringW`, que manipulan cadenas de distintos tipos de caracteres. Estos tipos de caracteres son del tipo TCHAR, **Char**y `wchar_t`, respectivamente. Estos tipos de cadena predeterminados usan un administrador de cadenas que asigna memoria del montón del proceso (en ATL) o del montón de CRT (en MFC). En el caso de las aplicaciones típicas, este esquema de asignación de memoria es suficiente. Sin embargo, para que el código Realice un uso intensivo de cadenas (o código multiproceso), es posible que los administradores de memoria predeterminados no funcionen de forma óptima. En este tema se describe cómo invalidar el comportamiento predeterminado de administración de memoria de `CStringT`, creando asignadores específicamente optimizados para la tarea en cuestión.

- [Implementación de un administrador de cadenas personalizado (método básico)](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)

- [Evitar la contención del montón](../atl-mfc-shared/avoidance-of-heap-contention.md)

- [Implementación de un administrador de cadenas personalizado (método avanzado)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)

- [CFixedStringT: un ejemplo de un administrador de cadenas personalizado](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)

## <a name="see-also"></a>Consulte también

[Ejemplo de CustomString](../overview/visual-cpp-samples.md)
