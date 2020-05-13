---
title: Error del compilador C2030
ms.date: 11/04/2016
f1_keywords:
- C2030
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
ms.openlocfilehash: e3f3936e6fd37da16c923cb482f45cec11833b3c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208037"
---
# <a name="compiler-error-c2030"></a>Error del compilador C2030

un destructor con accesibilidad 'protected private' no puede ser miembro de una clase declarada 'sealed'

Una clase de Windows en tiempo de ejecución declarada como `sealed` no puede tener un destructor privado protegido. En tipos sealed solo se permiten destructores no virtuales privados y virtuales públicos. Para obtener más información, consulte el artículo sobre [las clases de referencia y structs](../../cppcx/ref-classes-and-structs-c-cx.md).

Para corregir este error, cambie la accesibilidad del destructor.
