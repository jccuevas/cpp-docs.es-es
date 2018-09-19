---
title: Definiciones y declaraciones (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ae97ecc055ed7e6a448f2f820e762cafb2c5798
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028680"
---
# <a name="definitions-and-declarations-c"></a>Definiciones y declaraciones (C)

**Específicos de Microsoft**

La interfaz DLL hace referencia a todos los elementos (funciones y datos) que se sabe que se van a exportar mediante algún programa del sistema, es decir, todos los elementos declarados como **dllimport** o `dllexport`. Todas las declaraciones incluidas en la interfaz DLL deben especificar el atributo **dllimport** o `dllexport`. Sin embargo, la definición solo puede especificar el atributo `dllexport`. Por ejemplo, la definición de función siguiente genera un error del compilador:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int func()    /* Error; dllimport prohibited in */
                        /* definition. */
{
   return 1;
}
```

Este código también genera un error:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int i = 10;      /* Error; this is a definition. */
```

Sin embargo, esta es la sintaxis correcta:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport int i = 10;      /* Okay: this is an export definition. */
```

El uso de `dllexport` implica una definición, mientras que **dllimport** implica una declaración. Debe utilizar la palabra clave `extern` con `dllexport` para forzar una declaración; en caso contrario, se asume una definición.

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllImport int k;   /* These are correct and imply */
Dllimport int j;          /* a declaration. */
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Funciones de importación y exportación de archivos DLL](../c-language/dll-import-and-export-functions.md)