---
title: atributo de importación no_smart_pointers
ms.date: 08/29/2019
f1_keywords:
- no_smart_pointers
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
ms.openlocfilehash: 1fca3eb486ff3cfc7403c38e91855b799a698782
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220689"
---
# <a name="no_smart_pointers-import-attribute"></a>atributo de importación no_smart_pointers

**C++Cuestión**

Suprime la creación de punteros inteligentes para todas las interfaces en la biblioteca de tipos.

## <a name="syntax"></a>Sintaxis

> **#import** *biblioteca de tipos* **no_smart_pointers**

## <a name="remarks"></a>Comentarios

De forma predeterminada, cuando se utiliza `#import`, se obtiene una declaración de puntero inteligente para todas las interfaces de la biblioteca de tipos. Estos punteros inteligentes son del tipo [_com_ptr_t](../cpp/com-ptr-t-class.md).

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
