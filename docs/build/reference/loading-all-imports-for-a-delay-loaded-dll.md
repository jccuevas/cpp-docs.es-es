---
title: Cargar todas las importaciones para una archivo DLL para carga retrasada | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8afa206e62702407d9974802f9422c8597d772ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>Cargar todas las importaciones para un archivo DLL de carga retrasada
El **__HrLoadAllImportsForDll** función, que se define en delayhlp.cpp, indica al vinculador que cargue todas las importaciones desde un archivo DLL que se especificó con el [/DELAYLOAD](../../build/reference/delayload-delay-load-import.md) opción del vinculador.  
  
 Cargar todas las importaciones permite colocar en un lugar en el código de control de errores y no tiene que usar alrededor de las llamadas reales a las importaciones de control de excepciones. También se evita una situación donde la aplicación se produce un error parcial a través de un proceso como resultado el código auxiliar que se puede cargar una importación.  
  
 Al llamar a **__HrLoadAllImportsForDll** no cambia el comportamiento de los enlaces y error administrar; vea [notificación y control de errores](../../build/reference/error-handling-and-notification.md) para obtener más información.  
  
 El nombre del archivo DLL pasa a **__HrLoadAllImportsForDll** se compara con el nombre almacenado en el propio archivo DLL y distingue mayúsculas de minúsculas.  
  
 En el ejemplo siguiente se muestra cómo llamar a **__HrLoadAllImportsForDll**:  
  
```  
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {  
   printf ( "failed on snap load, exiting\n" );  
   exit(2);  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)