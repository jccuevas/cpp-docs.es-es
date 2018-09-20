---
title: Vinculación de miembros integrales Const estáticos ya No es Literal | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- literal attribute [C++]
- constants, declaring
- integral constant expressions
ms.assetid: d2a5e3d2-ffb0-4b61-8114-bec5993a1195
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c51853274b061ba290ff90993f45ccdf3375349b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431299"
---
# <a name="static-const-int-linkage-is-no-longer-literal"></a>La vinculación de miembros integrales const estáticos ya no es literal

Declaración de un miembro de constante de una clase ha cambiado de extensiones administradas para C++ a Visual C++.

Aunque `static const` todavía se admiten los miembros enteros, su atributo de vinculación ha cambiado. Su atributo de vinculación anterior ahora se realiza en un miembro entero literal. Por ejemplo, considere la siguiente clase de extensiones administradas:

```
public __gc class Constants {
public:
   static const int LOG_DEBUG = 4;
};
```

Esto genera los siguientes atributos de archivo de CIL subyacentes para el campo (tenga en cuenta el atributo literal):

```
.field public static literal int32
modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)
```

Si bien esto todavía se compila en la nueva sintaxis:

```
public ref class Constants {
public:
   static const int LOG_DEBUG = 4;
};
```

ya no emite el atributo literal y, por tanto, no se ve como una constante de tiempo de ejecución de CLR:

```
.field public static int32 modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)
```

Para tener el mismo atributo literal entre lenguaje, la declaración debe cambiarse a recién admitidas `literal` miembro de datos, tal como sigue,

```
public ref class Constants {
public:
   literal int LOG_DEBUG = 4;
};
```

## <a name="see-also"></a>Vea también

[Declaraciones de miembros en una clase o interfaz (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[literal](../windows/literal-cpp-component-extensions.md)