---
title: _set_controlfp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _set_controlfp
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
- set_controlfp
- _set_controlfp
dev_langs:
- C++
helpviewer_keywords:
- set_controlfp function
- floating-point functions, setting control word
- _set_controlfp function
ms.assetid: e0689d50-f68a-4028-a9c1-fb23eedee4ad
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: f7cf06b52624178a3d5bbe5907289eab7f57cbb5
ms.lasthandoff: 02/24/2017

---
# <a name="setcontrolfp"></a>_set_controlfp
Establece la palabra de control de punto flotante.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __cdecl _set_controlfp(  
    unsigned int newControl,  
    unsigned int mask  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `newControl`  
 Valores de bit de la nueva palabra de control.  
  
 `mask`  
 Máscara de los bits de la nueva palabra de control que se va a definir.  
  
## <a name="return-value"></a>Valor devuelto  
 Ninguno.  
  
## <a name="remarks"></a>Comentarios  
 `_set_controlfp` es similar a `_control87`, pero solo establece la palabra de control de punto flotante en `newControl`. Los bits de los valores indican el estado de control de punto flotante. El estado de control de punto flotante permite que el programa cambie los modos de precisión, redondeo e infinito en el paquete matemático de punto flotante. También puede aplicar o quitar una máscara a excepciones de punto flotante mediante `_set_controlfp`. Para obtener más información, vea [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md).  
  
 Esta función está desusada al compilar con [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) porque common language runtime sólo admite la precisión de punto flotante predeterminada.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|Compatibilidad|  
|-------------|---------------------|-------------------|  
|`_set_controlfp`|\<float.h>|Solo para procesadores x86|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [_clear87, _clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [_status87, _statusfp, _statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)
