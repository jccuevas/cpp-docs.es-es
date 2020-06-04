---
title: Operadores binarios
ms.date: 06/14/2018
helpviewer_keywords:
- member-selection operators [C++]
- operators [C++], binary
- binary operators [C++]
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
ms.openlocfilehash: 030ae71fec7a0d1572804f30d09f6f9b2749e436
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181309"
---
# <a name="binary-operators"></a>Operadores binarios

En la tabla siguiente se muestra una lista de operadores que se pueden sobrecargar.

## <a name="redefinable-binary-operators"></a>Operadores binarios redefinibles

|Operator|Nombre|
|--------------|----------|
|**,**|Coma|
|**!=**|Desigualdad|
|**%**|Modulus|
|**%=**|Módulo/asignación|
|**&**|AND bit a bit|
|**&&**|Y lógico|
|**&=**|AND bit a bit/asignación|
|**&#42;**|Multiplicación|
|**&#42;=**|Multiplicación/asignación|
|**+**|Suma|
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
|**&#124;&#124;**|O lógico|

Para declarar una función de operador binario como miembro no estático, debe declararla de la forma siguiente:

> *RET-Type* **operador** *OP* **(** *arg* **)**

donde *RET-Type* es el tipo de valor devuelto, *OP* es uno de los operadores enumerados en la tabla anterior y *arg* es un argumento de cualquier tipo.

Para declarar una función de operador binario como función global, debe declararla de la forma siguiente:

> *RET-Type* **operador** *OP* **(** _arg1_ **,** _arg2_ **)**

donde *RET-Type* y *OP* son como se describen para las funciones de operador de miembro y *arg1* y *arg2* son argumentos. Al menos uno de los argumentos debe ser de tipo de clase.

> [!NOTE]
> No hay restricciones para los tipos de valor devuelto de los operadores binarios; sin embargo, la mayoría de los operadores binarios definidos por el usuario devuelven un tipo de clase o una referencia a un tipo de clase.

## <a name="see-also"></a>Consulte también

[Sobrecarga de operadores](../cpp/operator-overloading.md)
