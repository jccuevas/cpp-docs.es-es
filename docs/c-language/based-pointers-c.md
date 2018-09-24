---
title: Punteros con base (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- __based keyword [C]
- based pointers
- pointers, based
- based addressing
ms.assetid: b5446920-89e0-4e2f-91f3-1f2a769a08e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 79e515a3f108d0857d2f8860566e14ee0acdefe3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097580"
---
# <a name="based-pointers-c"></a>Punteros con base (C)

**Específicos de Microsoft**

[__based (Referencia de C++)](../cpp/based-pointers-cpp.md)

Para los compiladores de 32 bits y 64 bits de Microsoft, un puntero de base es un desplazamiento de 32 bits o de 64 bits respecto a una base de puntero de 32 bits o de 64 bits. El direccionamiento de base es útil para el control de las secciones donde se asignan objetos, para reducir de esta manera el tamaño del archivo ejecutable y aumentar la velocidad de ejecución. En general, el formulario para especificar un puntero de base es

> *type* **__based(** *base* **)** *declarator*

La variante “basada en puntero” del direccionamiento de base permite la especificación de un puntero como base. El puntero de base, entonces, es un desplazamiento en la sección de memoria que se inicia al principio del puntero en el que se basa. Los punteros basados en direcciones de puntero son la única forma de la palabra clave `__based` válida en compilaciones de 32 bits y 64 bits. En tales compilaciones, son desplazamientos de 32 bits o de 64 bits respecto a una base de 32 bits o de 64 bits.

Uno de los usos de los punteros basados en punteros son los identificadores persistentes que contienen punteros. Una lista vinculada formada por punteros basados en un puntero se puede guardar en el disco y recargar en otro lugar de la memoria; los punteros seguirán siendo válidos.

En el ejemplo siguiente se muestra un puntero basado en un puntero.

```C
void *vpBuffer;

struct llist_t
{
    void __based( vpBuffer ) *vpData;
    struct llist_t __based( vpBuffer ) *llNext;
};
```

Al puntero `vpBuffer` se le asigna la dirección de memoria asignada posteriormente en el programa. La lista vinculada se reubica en relación con el valor de `vpBuffer`.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Declaradores y declaraciones de variables](../c-language/declarators-and-variable-declarations.md)