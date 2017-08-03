---
title: _setjmp3 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _setjmp3
apilocation:
- msvcrt.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- setjmp3
- _setjmp3
dev_langs:
- C++
helpviewer_keywords:
- _setjmp3 function
- setjmp3 function
ms.assetid: 6129c2f3-8bac-4fdb-a827-44e1eebba500
caps.latest.revision: 6
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 71a5963326e950c8e5c6aac629d1f428b189be18
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="setjmp3"></a>_setjmp3
Función de CRT interna. Nueva implementación de la función `setjmp`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _setjmp3(  
   OUT jmp_buf env,  
   int count,  
   (optional parameters)  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `env`  
 Dirección del búfer para almacenar la información de estado.  
  
 [in] `count`  
 Número de `DWORD` de información adicionales que hay almacenados en los `optional parameters`.  
  
 [in] `optional parameters`  
 Datos adicionales insertados por la función intrínseca `setjmp`. El primer `DWORD` es un puntero de función que sirve para desenredar datos extra y regresar a un estado de registro no volatile. El segundo `DWORD` es el nivel de intento que se va a restaurar. Cualquier otro dato extra se guarda en la matriz de datos genéricos de `jmp_buf`.  
  
## <a name="return-value"></a>Valor devuelto  
 Siempre devuelve 0.  
  
## <a name="remarks"></a>Comentarios  
 No use esta función en un programa de C++. Se trata de una función intrínseca que no admite C++. Para más información sobre cómo usar `setjmp`, vea [Usar setjmp/longjmp](../cpp/using-setjmp-longjmp.md).  
  
## <a name="requirements"></a>Requisitos  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [setjmp](../c-runtime-library/reference/setjmp.md)
