---
title: once (Pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.once
- once_CPP
helpviewer_keywords:
- once pragma
- pragmas, once
ms.assetid: c7517556-6403-4b16-8898-f2aa0a6f685f
ms.openlocfilehash: 643ad83b672f7b632925383972751a966256eb41
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220544"
---
# <a name="once-pragma"></a>once (Pragma)

Especifica que el compilador incluye el archivo de encabezado solo una vez, al compilar un archivo de código fuente.

## <a name="syntax"></a>Sintaxis

> **#pragma una vez**

## <a name="remarks"></a>Comentarios

El uso de `#pragma once` puede reducir los tiempos de compilación, ya que el compilador no abrirá y leerá el `#include` archivo de nuevo después del primer archivo en la unidad de traducción. Se denomina *optimización de inclusión múltiple*. Tiene un efecto similar a la expresión *include Guard* , que utiliza definiciones de macro de preprocesador para evitar la inclusión de varias inclusiones en el contenido del archivo. También ayuda a evitar infracciones de la *regla de una definición*, el requisito de que todas las plantillas, tipos, funciones y objetos no tengan más de una definición en el código.

Por ejemplo:

```cpp
// header.h
#pragma once
// Code placed here is included only once per translation unit
```

Se recomienda la directiva `#pragma once` para el nuevo código, ya que no contamina el espacio de nombres global con un símbolo de preprocesador. Requiere menos tipos, es menos molesto y no puede causar colisiones de *símbolos*, los errores que se producen cuando diferentes archivos de encabezado usan el mismo símbolo de preprocesador que el valor de protección. No forma parte del C++ estándar, pero lo implementan varios compiladores comunes.

No hay ninguna ventaja en el uso de la expresión include Guard y `#pragma once` en el mismo archivo. El compilador reconoce la expresión include Guard e implementa la optimización de inclusión múltiple de la misma manera que `#pragma once` la Directiva si ninguna directiva de preprocesador o código sin comentarios es anterior o posterior a la forma estándar de la expresión:

```cpp
// header.h
// Demonstration of the #include guard idiom.
// Note that the defined symbol can be arbitrary.
#ifndef HEADER_H_     // equivalently, #if !defined HEADER_H_
#define HEADER_H_
// Code placed here is included only once per translation unit
#endif // HEADER_H_
```

Se recomienda incluir la expresión de protección cuando el código debe ser portable a los compiladores que `#pragma once` no implementan la Directiva, para mantener la coherencia con el código existente o cuando no se puede realizar la optimización de varios includes. Puede producirse en proyectos complejos cuando los alias del sistema de archivos o las rutas de acceso de inclusión con alias impiden que el compilador identifique archivos de inclusión idénticos mediante una ruta canónica.

Tenga cuidado de no usar `#pragma once` o la expresión include Guard en archivos de encabezado diseñados para incluirse varias veces, que utilizan símbolos de preprocesador para controlar sus efectos. Para obtener un ejemplo de este diseño, vea \<el archivo de encabezado Assert. h >. También debe tener cuidado de administrar las rutas de acceso de inclusión para evitar la creación de varias rutas de acceso a archivos incluidos, lo que puede derrotar `#pragma once`la optimización de inclusión múltiple para las protecciones include y.

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
