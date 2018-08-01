---
title: Definiciones y declaraciones (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 951a7d5c4c171a6662c55d9ae7906cc1500cd137
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406736"
---
# <a name="definitions-and-declarations-c"></a>Definiciones y declaraciones (C++)
## <a name="microsoft-specific"></a>Específicos de Microsoft
 La interfaz DLL hace referencia a todos los elementos (funciones y datos) que se sabe que se puede exportar mediante algún programa en el sistema; es decir, todos los elementos que se declaran como **dllimport** o **dllexport**. Todas las declaraciones incluidas en la interfaz DLL deben especificar el **dllimport** o **dllexport** atributo. Sin embargo, la definición debe especificar solo el **dllexport** atributo. Por ejemplo, la definición de función siguiente genera un error del compilador:

```
__declspec( dllimport ) int func() {   // Error; dllimport
                                       // prohibited on definition.
   return 1;  
}
```

 Este código también genera un error:

```
__declspec( dllimport ) int i = 10;  // Error; this is a definition.
```

 Sin embargo, esta es la sintaxis correcta:

```
__declspec( dllexport ) int i = 10;  // Okay--export definition
```

 El uso de **dllexport** implica una definición, mientras que **dllimport** implica una declaración. Debe usar el **extern** palabra clave with **dllexport** para forzar una declaración; en caso contrario, se asume una definición. Por tanto, los siguientes ejemplos son correctos:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllExport int k; // These are both correct and imply a
DllImport int j;        // declaration.
```

 Los ejemplos siguientes aclaran los anteriores:

```
static __declspec( dllimport ) int l; // Error; not declared extern.

void func() {
    static __declspec( dllimport ) int s;  // Error; not declared
                                           // extern.
    __declspec( dllimport ) int m;         // Okay; this is a
                                           // declaration.
    __declspec( dllexport ) int n;         // Error; implies external
                                           // definition in local scope.
    extern __declspec( dllimport ) int i;  // Okay; this is a
                                           // declaration.
    extern __declspec( dllexport ) int k;  // Okay; extern implies
                                           // declaration.
    __declspec( dllexport ) int x = 5;     // Error; implies external
                                           // definition in local scope.
}
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)