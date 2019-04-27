---
title: Operadores binarios
ms.date: 06/14/2018
helpviewer_keywords:
- member-selection operators [C++]
- operators [C++], binary
- binary operators [C++]
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
ms.openlocfilehash: 700d8fd784862c3e9f81fcde839063ff0a4696bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176660"
---
# <a name="binary-operators"></a>Operadores binarios

En la tabla siguiente se muestra una lista de operadores que se pueden sobrecargar.

## <a name="redefinable-binary-operators"></a>Operadores binarios redefinibles

|Operador|Name|
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

> *ret-type* **operator** *op* **(** *arg* **)**

donde *ret-type* es el tipo de valor devuelto, *op* es uno de los operadores se indican en la tabla anterior, y *arg* es un argumento de cualquier tipo.

Para declarar una función de operador binario como función global, debe declararla de la forma siguiente:

> *ret-type* **operator** *op* **(** _arg1_**,** _arg2_ **)**

donde *ret-type* y *op* son descrito para las funciones de operador de miembro y *arg1* y *arg2* son argumentos. Al menos uno de los argumentos debe ser de tipo de clase.

> [!NOTE]
> No hay restricciones para los tipos de valor devuelto de los operadores binarios; sin embargo, la mayoría de los operadores binarios definidos por el usuario devuelven un tipo de clase o una referencia a un tipo de clase.

## <a name="see-also"></a>Vea también

[Sobrecarga de operadores](../cpp/operator-overloading.md)