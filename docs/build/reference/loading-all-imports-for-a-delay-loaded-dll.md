---
title: Cargar todas las importaciones para un archivo DLL de carga retrasada
ms.date: 11/04/2016
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
ms.openlocfilehash: e855b648dc7a9ee0670c3704a11aa1897a238403
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301674"
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>Cargar todas las importaciones para un archivo DLL de carga retrasada

El **__HrLoadAllImportsForDll** función, que se define en delayhlp.cpp, indica al vinculador que todas las importaciones de carga desde un archivo DLL que se especificó con el [/DELAYLOAD](delayload-delay-load-import.md) opción del vinculador.

Cargar todas las importaciones le permite colocar en un mismo lugar en el código de control de errores y no tiene que usar en torno a las llamadas reales para las importaciones de control de excepciones. También evita una situación donde la aplicación se produce un error parcialmente a través de un proceso como resultado el código auxiliar no se puede cargar una importación.

Una llamada a **__HrLoadAllImportsForDll** no cambia el comportamiento de los enlaces y error de control; vea [notificación y control de errores](error-handling-and-notification.md) para obtener más información.

El nombre del archivo DLL que se pasa a **__HrLoadAllImportsForDll** se compara con el nombre almacenado en el propio archivo DLL y distingue mayúsculas de minúsculas.

El ejemplo siguiente muestra cómo llamar a **__HrLoadAllImportsForDll**:

```
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {
   printf ( "failed on snap load, exiting\n" );
   exit(2);
}
```

## <a name="see-also"></a>Vea también

[Compatibilidad del vinculador con las DLL de carga retrasada](linker-support-for-delay-loaded-dlls.md)
