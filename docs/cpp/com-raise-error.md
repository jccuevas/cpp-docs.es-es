---
title: _com_raise_error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_raise_error
dev_langs:
- C++
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f38a0d97b90f1512e5f16b3bd147bda3e0614e4f
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944475"
---
# <a name="comraiseerror"></a>_com_raise_error
**Específicos de Microsoft**  
  
 Se produce un [_com_error](../cpp/com-error-class.md) en respuesta a un error.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
void __stdcall _com_raise_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = 0  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *recursos humanos*  
 Información de HRESULT.  
  
 *perrinfo*  
 Objeto `IErrorInfo`.  
  
## <a name="remarks"></a>Comentarios  
 `_com_raise_error`, que se define en \<comdef.h >, se puede reemplazar por una versión escrita por el usuario del mismo nombre y prototipo. Esto se podría hacer si se desea utilizar `#import` pero no se desea utilizar el control de excepciones de C++. En ese caso, una versión de usuario de `_com_raise_error` podría decidir hacer un `longjmp` o mostrar un cuadro de mensaje y detener. La versión de usuario no debe volver, sin embargo, porque el código de compatibilidad con COM del compilador no espera que vuelva.  
  
 También puede usar [_set_com_error_handler](../cpp/set-com-error-handler.md) para reemplazar la función de control de errores de forma predeterminada.  
  
 De forma predeterminada, `_com_raise_error` se define de la manera siguiente:  
  
```cpp  
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {  
   throw _com_error(hr, perrinfo);  
}  
```  
  
**FIN de Específicos de Microsoft**  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<comdef.h >  
  
 **Lib:** si el **wchar_t es tipo nativo** opción del compilador está activada, use omsuppw.lib o comsuppwd.lib. Si **wchar_t es tipo nativo** está desactivada, use comsupp.lib. Para obtener más información, vea [/Zc:wchar_t (wchar_t es un tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).  
  
## <a name="see-also"></a>Vea también  
 [Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)   
 [_set_com_error_handler](../cpp/set-com-error-handler.md)