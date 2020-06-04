---
title: Definiciones y declaraciones (C++)
ms.date: 11/04/2016
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
ms.openlocfilehash: 20683f3d2e12f7ffead573cbac46fdd4e106c383
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189382"
---
# <a name="definitions-and-declarations-c"></a>Definiciones y declaraciones (C++)

**Específicos de Microsoft**

La interfaz DLL hace referencia a todos los elementos (funciones y datos) que se sabe que se van a exportar mediante algún programa del sistema; es decir, todos los elementos que se declaran como **DllImport** o **dllexport**. Todas las declaraciones incluidas en la interfaz DLL deben especificar el atributo **DllImport** o **dllexport** . Sin embargo, la definición solo debe especificar el atributo **dllexport** . Por ejemplo, la definición de función siguiente genera un error del compilador:

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

El uso de **dllexport** implica una definición, mientras que **DllImport** implica una declaración. Debe utilizar la palabra clave **extern** con **dllexport** para forzar una declaración; de lo contrario, se implica una definición. Por tanto, los siguientes ejemplos son correctos:

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

## <a name="see-also"></a>Consulte también

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
