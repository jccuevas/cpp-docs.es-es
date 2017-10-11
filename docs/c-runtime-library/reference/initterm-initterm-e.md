---
title: _initterm, _initterm_e | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _initterm_e
- _initterm
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
- _initterm_e
- initterm
- _initterm
- initterm_e
dev_langs:
- C++
helpviewer_keywords:
- initterm function
- initterm_e function
- _initterm function
- _initterm_e function
ms.assetid: 85131efe-c747-429a-8897-bcdedb000172
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 377f8e19268a643b0237da66ba14a82fc7b6685b
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="initterm-initterme"></a>_initterm, _initterm_e
Métodos internos que recorren una tabla de punteros de función y los inicializan.  
  
 El primer puntero es la ubicación inicial de la tabla y el segundo puntero, la ubicación final.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __cdecl _initterm(  
   PVFV *,  
   PVFV *  
);  
  
int __cdecl _initterm_e(  
   PVFV *,  
   PVFV *  
);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un código de error distinto de cero si se produce un error de inicialización y genera un error; 0 si no se produce ningún error.  
  
## <a name="remarks"></a>Comentarios  
 Estos métodos solo se llaman internamente durante la inicialización de un programa de C++. No llame a estos métodos en un programa.  
  
 Cuando estos métodos recorren una tabla de entradas de función, omiten las entradas `NULL` y continúan.  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)
