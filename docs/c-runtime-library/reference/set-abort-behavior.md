---
title: _set_abort_behavior | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _set_abort_behavior
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_abort_behavior
- set_abort_behavior
dev_langs:
- C++
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
ms.assetid: 43918766-e4ba-4b1f-80e8-1a4a910cd452
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: edf31ccddfb9ab2eaa6de226ff4ec7eb09869438
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="setabortbehavior"></a>_set_abort_behavior
Especifica la acción que se debe llevar a cabo cuando un programa finaliza de forma anormal.  
  
> [!NOTE]
>  No use la función `abort` para cerrar una aplicación de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)], salvo en escenarios de prueba o de depuración. Las formas de cerrar una aplicación de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] mediante programación o con la interfaz de usuario no están permitidas según los [requisitos para la certificación de aplicaciones de Windows 8](http://go.microsoft.com/fwlink/?LinkId=262889). Para obtener más información, consulte [Ciclo de vida de la aplicación (aplicaciones de la Tienda Windows)](http://go.microsoft.com/fwlink/?LinkId=262853).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned int _set_abort_behavior(  
   unsigned int flags,  
   unsigned int mask  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `flags`  
 Nuevo valor de las marcas `abort`.  
  
 [in] `mask`  
 Máscara para los bits de las marcas `abort` que se deben establecer.  
  
## <a name="return-value"></a>Valor devuelto  
 Valor anterior de las marcas.  
  
## <a name="remarks"></a>Comentarios  
 Hay dos marcas `abort`: `_WRITE_ABORT_MSG` y `_CALL_REPORTFAULT`. `_WRITE_ABORT_MSG` determina si se imprime un mensaje de texto de ayuda cuando un programa finaliza de forma anormal. El mensaje indica que la aplicación ha llamado a la función `abort`. El comportamiento predeterminado consiste en imprimir el mensaje. `_CALL_REPORTFAULT` (si se establece) especifica que se genera y notifica un volcado de memoria Watson cuando se llama a `abort`. De forma predeterminada, los informes de volcado de memoria están habilitados en las compilaciones que no son de DEBUG.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_set_abort_behavior`|\<stdlib.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```C  
// crt_set_abort_behavior.c  
// compile with: /TC  
#include <stdlib.h>  
  
int main()  
{  
   printf("Suppressing the abort message. If successful, this message"  
          " will be the only output.\n");  
   // Suppress the abort message  
   _set_abort_behavior( 0, _WRITE_ABORT_MSG);  
   abort();  
}  
```  
  
```Output  
Suppressing the abort message. If successful, this message will be the only output.  
```  
  
## <a name="see-also"></a>Vea también  
 [abort](../../c-runtime-library/reference/abort.md)
