---
title: exception (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- exception
dev_langs:
- C++
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec1cfe2be7f6a2172b6624f15cb3dcde4f0ba3c2
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957023"
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
