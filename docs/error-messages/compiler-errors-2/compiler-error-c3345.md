---
title: Error del compilador C3345 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3345
dev_langs:
- C++
helpviewer_keywords:
- C3345
ms.assetid: 1dda4c79-73bb-441b-b939-746154c3afba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 191c2184d14f991ab62f439b492c7fd7f4a00be5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118952"
---
# <a name="compiler-error-c3345"></a>Error del compilador C3345

'identifier': identificador no válido para el nombre de módulo

El elemento *identifier* de un módulo contiene uno o más caracteres no aceptados. Un identificador es válido si el primer carácter es una letra, un carácter de subrayado o un carácter ANSI (0x80-FF) alto y cualquier carácter posterior es alfanumérico, un carácter de subrayado o un carácter ANSI alto.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Asegúrese de que el elemento *identifier* no contenga espacios en blanco u otros caracteres inaceptables.

## <a name="example"></a>Ejemplo

El ejemplo de código siguiente causa el mensaje de error C3345 porque el parámetro `name` del atributo `module` contiene un espacio en blanco.

```
// cpp_attr_name_module.cpp
// compile with: /LD /link /OPT:NOREF
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

// C3345 expected
[module(dll, name="My Library", version="1.2", helpfile="MyHelpFile")]
// Try the following line instead
//[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]
// Module attribute now applies to this class
class CMyClass {
public:
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {
   // add your own code here
   return __super::DllMain(dwReason, lpReserved);
   }
};
```

## <a name="see-also"></a>Vea también

[__iscsym](../../c-runtime-library/reference/iscsym-functions.md)<br/>
[Clasificación de caracteres](../../c-runtime-library/character-classification.md)<br/>
[módulo](../../windows/module-cpp.md)