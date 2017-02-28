---
title: _inp, _inpw, _inpd | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _inp
- _inpw
- _inpd
apilocation:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- inpd
- _inp
- _inpw
- _inpd
dev_langs:
- C++
helpviewer_keywords:
- inp function
- inpw function
- ports, I/O routines
- inpd function
- _inp function
- _inpd function
- I/O [CRT], port
- _inpw function
ms.assetid: 5d9c2e38-fc85-4294-86d5-7282cc02d1b3
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 54325f60b0d1714cab68f17152609a8980bc2a60
ms.lasthandoff: 02/24/2017

---
# <a name="inp-inpw-inpd"></a>_inp, _inpw, _inpd
Especifica, desde un puerto, un byte (`_inp`), una palabra (`_inpw`) o una palabra doble (`_inpd`).  
  
> [!IMPORTANT]
>  Estas funciones están obsoletas. A partir de Visual Studio 2015, no están disponibles en CRT.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _inp(   
   unsigned short port   
);  
unsigned short _inpw(   
   unsigned short port   
);  
unsigned long _inpd(   
   unsigned short port   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `port`  
 Número de puerto de E/S.  
  
## <a name="return-value"></a>Valor devuelto  
 Las funciones devuelven el byte, la palabra o la palabra doble leída en `port`. No se devuelve ningún error.  
  
## <a name="remarks"></a>Comentarios  
 Las funciones `_inp`, `_inpw`y `_inpd` leen un byte, una palabra y una palabra doble, respectivamente, del puerto de conexión especificado. El valor de entrada puede ser cualquier entero corto sin signo del intervalo comprendido entre 0 y 65.535.  
  
 Dado que estas funciones leen directamente desde un puerto de E/S, no se pueden usar en código de usuario en Windows NT, Windows 2000, Windows XP y Windows Server 2003.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_inp`|\<conio.h>|  
|`_inpw`|\<conio.h>|  
|`_inpd`|\<conio.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../c-runtime-library/crt-library-features.md).  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [E/S de consola y de puerto](../c-runtime-library/console-and-port-i-o.md)   
 [_outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)
