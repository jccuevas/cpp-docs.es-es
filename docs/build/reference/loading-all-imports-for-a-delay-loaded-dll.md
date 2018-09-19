---
title: Cargar todas las importaciones para un archivo DLL de carga retrasada | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29ef1c576af7930e157dafd0f57bf0b8dff49fa6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715590"
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>Cargar todas las importaciones para un archivo DLL de carga retrasada

El **__HrLoadAllImportsForDll** función, que se define en delayhlp.cpp, indica al vinculador que todas las importaciones de carga desde un archivo DLL que se especificó con el [/DELAYLOAD](../../build/reference/delayload-delay-load-import.md) opción del vinculador.

Cargar todas las importaciones le permite colocar en un mismo lugar en el código de control de errores y no tiene que usar en torno a las llamadas reales para las importaciones de control de excepciones. También evita una situación donde la aplicación se produce un error parcialmente a través de un proceso como resultado el código auxiliar no se puede cargar una importación.

Una llamada a **__HrLoadAllImportsForDll** no cambia el comportamiento de los enlaces y error de control; vea [notificación y control de errores](../../build/reference/error-handling-and-notification.md) para obtener más información.

El nombre del archivo DLL que se pasa a **__HrLoadAllImportsForDll** se compara con el nombre almacenado en el propio archivo DLL y distingue mayúsculas de minúsculas.

El ejemplo siguiente muestra cómo llamar a **__HrLoadAllImportsForDll**:

```
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {
   printf ( "failed on snap load, exiting\n" );
   exit(2);
}
```

## <a name="see-also"></a>Vea también

[Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)