---
title: once
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.once
- once_CPP
helpviewer_keywords:
- once pragma
- pragmas, once
ms.assetid: c7517556-6403-4b16-8898-f2aa0a6f685f
ms.openlocfilehash: 6061fe77960aa64e2dcb39db05897ef0e7fb5f2e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039889"
---
# <a name="once"></a>once
Especifica que el compilador incluirá (abrirá) el archivo una sola vez al compilar un archivo de código fuente.

## <a name="syntax"></a>Sintaxis

```
#pragma once
```

## <a name="remarks"></a>Comentarios

El uso de `#pragma once` puede reducir los tiempos de compilación como el compilador no abrirá y leerá el archivo después del primer `#include` del archivo en la unidad de traducción. Esto se conoce como *optimización de inclusión múltiple*. Tiene un efecto similar a la `#include guard` locución, que usa las definiciones de macro de preprocesador para evitar la inclusión múltiple del contenido del archivo. Esto también ayuda a evitar infracciones de la *regla de una definición*: el requisito de que todas las plantillas, tipos, funciones y objetos tengan no más de una definición en el código.

Por ejemplo:

```
// header.h
#pragma once
// Code placed here is included only once per translation unit
```

Se recomienda la directiva `#pragma once` para el nuevo código, ya que no contamina el espacio de nombres global con un símbolo de preprocesador. Requiere escribir menos, es menos confuso y no puede causar colisiones de símbolos (errores generados cuando archivos de encabezado diferentes usan el mismo símbolo de preprocesador como valor de protección. No forma parte del estándar de C++, pero varios compiladores comunes la implementan de forma portátil.

No existe ninguna ventaja en usar la expresión #include guard y `#pragma once` en el mismo archivo. El compilador reconoce la expresión #include guard e implementa la optimización de inclusión de la misma manera que la directiva `#pragma once` si el código que no es comentario o la directiva de preprocesador viene antes o después de la forma estándar de la expresión:

```
// header.h
// Demonstration of the #include guard idiom.
// Note that the defined symbol can be arbitrary.
#ifndef HEADER_H_     // equivalently, #if !defined HEADER_H_
#define HEADER_H_
// Code placed here is included only once per translation unit
#endif // HEADER_H_
```

Se recomienda la `#include guard` modismo cuando el código debe poder migrarse a los compiladores que no implementan la `#pragma once` directiva, para mantener la coherencia con el código existente, o cuando la inclusión múltiple optimización es imposible. Esto puede ocurrir en proyectos complejos cuando los alias de sistema de archivos o las rutas de acceso de inclusión con alias evitan que el compilador identifique archivos de inclusión idénticos mediante la ruta de acceso canónica.

Tenga cuidado de no usar `#pragma once` o `#include guard` modismo en archivos de encabezado que están diseñados para incluirse varias veces, con símbolos de preprocesador para controlar sus efectos. Para obtener un ejemplo de este diseño, vea el \<assert.h > archivo de encabezado. También cuidado al administrar incluir rutas de acceso para evitar la creación de varias rutas de acceso a los archivos incluidos, que pueden anular la inclusión múltiple tanto para la optimización `#include guard`s y `#pragma once`.

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)