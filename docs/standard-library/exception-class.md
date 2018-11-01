---
title: Clase exception
ms.date: 11/04/2016
f1_keywords:
- exception
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
ms.openlocfilehash: 009ef74d810976eb9f054b45e388ceb0fe612b2e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521047"
---
# <a name="exception-class"></a>Clase exception

La clase actúa como clase base para todas las excepciones iniciadas por determinadas expresiones y por la biblioteca estándar de C++.

## <a name="syntax"></a>Sintaxis

```cpp
class exception {
   public:
   exception();
   exception(const char* const &message);
   exception(const char* const &message, int);
   exception(const exception &right);
   exception& operator=(const exception &right);
   virtual ~exception();
   virtual const char *what() const;
   };
```

## <a name="remarks"></a>Comentarios

En concreto, esta clase base es la raíz de las clases de excepción estándar definidas en [\<stdexcept>](../standard-library/stdexcept.md). El constructor predeterminado no especifica el valor de cadena de C devuelto por `what`, pero lo pueden definir los constructores de ciertas clases derivadas como una cadena de C definida por la implementación. Ninguna de las funciones miembro produce excepciones.

El **int** parámetro le permite especificar que no se debe asignar ninguna memoria. El valor de la **int** se omite.

> [!NOTE]
> Los constructores `exception(const char* const &message)` y `exception(const char* const &message, int)` son extensiones de Microsoft para la biblioteca estándar de C++.

## <a name="example"></a>Ejemplo

Para obtener ejemplos del uso de las clases de excepción estándar que heredan de la clase `exception`, vea cualquiera de las clases definidas en [\<stdexcept>](../standard-library/stdexcept.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<exception>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
