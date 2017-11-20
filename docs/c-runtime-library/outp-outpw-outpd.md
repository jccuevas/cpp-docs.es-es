---
title: _outp, _outpw, _outpd | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _outpd
- _outp
- _outpw
apilocation:
- msvcrt.dll
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- _outpw
- _outpd
- _outp
- outpd
dev_langs: C++
helpviewer_keywords:
- outpw function
- words
- _outpd function
- outpd function
- outp function
- ports, writing bytes at
- bytes, writing to ports
- words, writing to ports
- double words
- double words, writing to ports
- _outpw function
- _outp function
ms.assetid: c200fe22-41f6-46fd-b0be-ebb805b35181
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ac8f0cd386d8fece71f47b5c3d2048bead7cca1b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="outp-outpw-outpd"></a>_outp, _outpw, _outpd
Genera, en un puerto, un byte (`_outp`), una palabra (`_outpw`) o a una palabra doble (`_outpd`).  
  
> [!IMPORTANT]
>  Estas funciones están obsoletas. A partir de Visual Studio 2015, no están disponibles en CRT.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      int _outp(  
unsigned short port,  
int databyte   
);  
unsigned short _outpw(  
unsigned short port,  
unsigned short dataword   
);  
unsigned long _outpd(  
unsigned short port,  
unsigned long dataword   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *port*  
 Número de puerto.  
  
 *databyte, dataword*  
 Valores de salida.  
  
## <a name="return-value"></a>Valor devuelto  
 Las funciones devuelven el resultado de datos. No se devuelve ningún error.  
  
## <a name="remarks"></a>Comentarios  
 Las funciones `_outp`, `_outpw`y `_outpd` escriben un byte, una palabra y una palabra doble, respectivamente, en el puerto de salida especificado. El argumento de *port* puede ser cualquier entero sin signo del intervalo comprendido entre 0 y 65 535; *databyte* puede ser cualquier entero del intervalo comprendido entre 0 y 255; y *dataword* puede ser cualquier valor del intervalo de un entero, un entero corto sin signo y un entero largo sin signo.  
  
 Dado que estas funciones escriben directamente en un puerto de E/S, no se pueden usar en código de usuario en Windows NT, Windows 2000, Windows XP y Windows Server 2003. Para obtener información sobre el uso de puertos de E/S en estos sistemas operativos, busque “Comunicaciones serie en Win32” en MSDN.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_outp`|\<conio.h>|  
|`_outpw`|\<conio.h>|  
|`_outpd`|\<conio.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Vea también  
 [E/S de consola y de puerto](../c-runtime-library/console-and-port-i-o.md)   
 [_inp, _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)