---
title: Error del compilador C2558
ms.date: 11/04/2016
f1_keywords:
- C2558
helpviewer_keywords:
- C2558
ms.assetid: 822b701e-dcae-423a-b21f-47f36aff9c90
ms.openlocfilehash: 93b6e414f26c56702a1c7ac12863cbcd5063b570
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177500"
---
# <a name="compiler-error-c2558"></a>Error del compilador C2558

'identificador' : no hay un constructor de copias disponible o éste se declaró como 'explicit'

Un constructor de copias inicializa un objeto a partir de otro objeto del mismo tipo. (Realiza una copia del objeto). El compilador genera un constructor de copias predeterminado si no se define ningún constructor.

### <a name="to-fix-this-error"></a>Para solucionar este error

1. El problema puede producirse cuando se intenta copiar una clase cuyo constructor de copias es `private`. En la mayoría de los casos, no debe copiarse una clase que tenga un constructor de copias `private`. Una técnica de programación común consiste en declarar un constructor de copias `private` para impedir el uso directo de una clase. La clase puede quedar inservible o requerir otra clase para poder funcionar correctamente.

   Si determina que es seguro utilizar una clase que tenga un constructor de copias `private`, derive una nueva clase a partir de la clase que tiene el constructor `private` y proporcione un constructor de copias `public` o `protected` en la clase nueva. Utilice la clase derivada en lugar de la original.

1. El problema puede producirse cuando se intenta copiar una clase cuyo constructor de copias es explicit. Declarar un constructor de copias como `explicit` impide que se pasen objetos de una clase a las funciones o que se devuelvan objetos de una clase desde las funciones. Para obtener más información sobre los constructores explícitos, vea [conversiones de tipos definidos por el usuario](../../cpp/user-defined-type-conversions-cpp.md).

1. El problema puede producirse cuando intenta copiar una instancia de la clase declarada como `const` utilizando un constructor de copias que no toma un parámetro de referencia `const`. Declare el constructor de copias con una referencia de tipo `const` en lugar de con una referencia de otro tipo.
