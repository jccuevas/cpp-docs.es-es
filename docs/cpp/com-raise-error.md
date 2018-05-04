---
title: _com_raise_error | Documentos de Microsoft
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
ms.openlocfilehash: 4e7b28c9d48704eede883cbcd387d9e77798647f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="comraiseerror"></a>_com_raise_error
**Específicos de Microsoft**  
  
 Produce una [_com_error](../cpp/com-error-class.md) en respuesta a un error.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      void __stdcall _com_raise_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = 0  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hr`  
 Información de `HRESULT`.  
  
 `perrinfo`  
 **IErrorInfo** objeto.  
  
## <a name="remarks"></a>Comentarios  
 `_com_raise_error`, que se define en \<comdef.h >, se pueden reemplazar por una versión del mismo nombre y prototipo escritos por el usuario. Esto se podría hacer si se desea utilizar `#import` pero no se desea utilizar el control de excepciones de C++. En ese caso, una versión de usuario de **_com_raise_error** podría resultar útil un `longjmp` o mostrar un cuadro de mensaje y detener. La versión de usuario no debe volver, sin embargo, porque el código de compatibilidad con COM del compilador no espera que vuelva.  
  
 También puede usar [_set_com_error_handler](../cpp/set-com-error-handler.md) para reemplazar la función de control de errores predeterminado.  
  
 De forma predeterminada, `_com_raise_error` se define de la manera siguiente:  
  
```  
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {  
   throw _com_error(hr, perrinfo);  
}  
```  
  
**FIN de Específicos de Microsoft**  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<comdef.h >  
  
 **Lib:** si la **wchar_t es tipo nativo** opción del compilador está activada, use omsuppw.lib o comsuppwd.lib. Si **wchar_t es tipo nativo** está desactivada, use comsupp.lib. Para obtener más información, vea [/Zc:wchar_t (wchar_t es un tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).  
  
## <a name="see-also"></a>Vea también  
 [Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)   
 [_set_com_error_handler](../cpp/set-com-error-handler.md)