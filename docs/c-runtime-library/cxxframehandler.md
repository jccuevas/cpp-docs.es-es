---
title: __CxxFrameHandler | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __CxxFrameHandler
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- __CxxFrameHandler
dev_langs:
- C++
helpviewer_keywords:
- __CxxFrameHandler
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
caps.latest.revision: 3
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
ms.openlocfilehash: 9798d46172aac730abaebe8ee2a9c4015422655c
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="cxxframehandler"></a>__CxxFrameHandler
Función de CRT interna. CRT la usa para controlar los marcos de excepción estructurados.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
EXCEPTION_DISPOSITION __CxxFrameHandler(  
      EHExceptionRecord  *pExcept,  
      EHRegistrationNode *pRN,  
      void               *pContext,   
      DispatcherContext  *pDC  
   )  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pExcept`  
 Registro de excepción que se pasa a las posibles instrucciones `catch`.  
  
 `pRN`  
 Información dinámica sobre el marco de pila que se usa para controlar la excepción. Para más información, vea ehdata.h.  
  
 `pContext`  
 Contexto. (No se usa en procesadores Intel).  
  
 `pDC`  
 Información extra sobre la entrada de la función y el marco de pila.  
  
## <a name="return-value"></a>Valor devuelto  
 Uno de los valores de *expresión de filtro* usado por la [instrucción try-except](../cpp/try-except-statement.md).  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|__CxxFrameHandler|excpt.h, ehdata.h|
