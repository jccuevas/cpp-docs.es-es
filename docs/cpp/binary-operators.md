---
title: Los operadores binarios | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- member-selection operators [C++]
- operators [C++], binary
- binary operators [C++]
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c5ad5997657ce9f8a61383a2cd7e685f0a28751
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036558"
---
# <a name="binary-operators"></a>Operadores binarios

En la tabla siguiente se muestra una lista de operadores que se pueden sobrecargar.

## <a name="redefinable-binary-operators"></a>Operadores binarios redefinibles

|Operador|nombre|
|--------------|----------|
|**,**|Coma|
|**\!=**|Desigualdad|
|**%**|Módulo|
|**%=**|Módulo/asignación|
|**&**|AND bit a bit|
|**&&**|AND lógico|
|**&=**|AND bit a bit/asignación|
|**&#42;**|Multiplicación|
|**&#42;=**|Multiplicación/asignación|
|**+**|Adición|
|**+=**|Suma/asignación|
|**-**|Resta|
|**-=**|Resta/asignación|
|**->**|Selección de miembro|
|**->&#42;**|Selección de puntero a miembro|
|**/**|División|
|**/=**|División/asignación|
|**<**|Menor que|
|**<<**|Desplazamiento a la izquierda|
|**<<=**|Desplazamiento a la izquierda/asignación|
|**<=**|Menor o igual que|
|**=**|Asignación|
|**==**|Igualdad|
|**>**|Mayor que|
|**>=**|Mayor o igual que|
|**>>**|Desplazamiento a la derecha|
|**>>=**|Desplazamiento a la derecha/asignación|
|**^**|OR exclusivo|
|**^=**|OR exclusivo/asignación|
|**&#124;**|OR inclusivo bit a bit|
|**&#124;=**|OR inclusivo bit a bit/asignación|
|**&#124;&#124;**|OR lógico|

Para declarar una función de operador binario como miembro no estático, debe declararla de la forma siguiente:

> *RET-type* **operador** *op* **(** *arg* **)**

donde *ret-type* es el tipo de valor devuelto, *op* es uno de los operadores se indican en la tabla anterior, y *arg* es un argumento de cualquier tipo.

Para declarar una función de operador binario como función global, debe declararla de la forma siguiente:

> *RET-type* **operador** *op* **(** _arg1_**,** _arg2_ **)**

donde *ret-type* y *op* son descrito para las funciones de operador de miembro y *arg1* y *arg2* son argumentos. Al menos uno de los argumentos debe ser de tipo de clase.

> [!NOTE]
> No hay restricciones para los tipos de valor devuelto de los operadores binarios; sin embargo, la mayoría de los operadores binarios definidos por el usuario devuelven un tipo de clase o una referencia a un tipo de clase.

## <a name="see-also"></a>Vea también

[Sobrecarga de operadores](../cpp/operator-overloading.md)