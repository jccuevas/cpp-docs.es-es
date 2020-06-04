---
title: Macros y C++
ms.date: 08/29/2019
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
ms.openlocfilehash: 8a86fb81544af91d4e844fb08b7948a589976e04
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220805"
---
# <a name="macros-and-c"></a>Macros y C++

C++ofrece nuevas capacidades, algunas de las cuales suplantan a las ofrecidas por el preprocesador de ANSI C. Estas nuevas capacidades mejoran la seguridad de tipos y la previsibilidad del lenguaje:

- En C++, los objetos declarados como **const** se pueden usar en expresiones constantes. Permite a los programas declarar constantes que tienen información de tipo y valor. Pueden declarar enumeraciones que se pueden ver simbólicamente con el depurador. Cuando se usa la `#define` Directiva de preprocesador para definir constantes, no es tan precisa y no tiene seguridad de tipos. No se asigna ningún almacenamiento para un objeto **const** , a menos que el programa contenga una expresión que tome su dirección.

- La capacidad de función insertada de C++ suplanta las macros de tipo de función. Las ventajas de utilizar funciones insertadas respecto a macros son:

  - Seguridad de tipos. Las funciones insertadas están sujetas a la misma comprobación de tipos que las funciones normales. Las macros no tienen seguridad de tipos.

  - Se corrige el control de argumentos que tienen efectos secundarios. Las funciones insertadas evalúan las expresiones proporcionadas como argumentos antes de que se escriba el cuerpo de la función. Por lo tanto, no hay ninguna posibilidad de que una expresión con efectos secundarios no sea segura.

Para obtener más información sobre las funciones insertadas, vea [Inline, \_](../cpp/inline-functions-cpp.md)_ _ Inline, _forceinline.

Por compatibilidad con versiones anteriores, todos los servicios de preprocesador que existían en ANSI C y en las especificaciones anteriores de C++ se conservan para Microsoft C++.

## <a name="see-also"></a>Vea también

[Macros predefinidas](../preprocessor/predefined-macros.md)\
[Macros (C/C++)](../preprocessor/macros-c-cpp.md)
