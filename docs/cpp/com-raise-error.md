---
title: "_com_raise_error | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_raise_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_com_raise_error (función)"
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_raise_error
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Produce un [\_com\_error](../cpp/com-error-class.md) en respuesta a un error.  
  
## Sintaxis  
  
```  
  
      void __stdcall _com_raise_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = 0  
);  
```  
  
#### Parámetros  
 `hr`  
 Información de `HRESULT`.  
  
 `perrinfo`  
 Objeto **IErrorInfo**.  
  
## Comentarios  
 `_com_raise_error`, que se define en comdef.h, se puede reemplazar por una versión escrita por el usuario con el mismo nombre y prototipo.  Esto se podría hacer si se desea utilizar `#import` pero no se desea utilizar el control de excepciones de C\+\+.  En ese caso, una versión de usuario de **\_com\_raise\_error** podría decidir hacer `longjmp` o mostrar un cuadro de mensaje y detenerse.  La versión de usuario no debe volver, sin embargo, porque el código de compatibilidad con COM del compilador no espera que vuelva.  
  
 También puede utilizar [\_set\_com\_error\_handler](../cpp/set-com-error-handler.md) para reemplazar la función predeterminada de control de errores.  
  
 De forma predeterminada, `_com_raise_error` se define de la manera siguiente:  
  
```  
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {  
   throw _com_error(hr, perrinfo);  
}  
```  
  
## FIN de Específicos de Microsoft  
  
## Requisitos  
 **Encabezado:** comdef.h  
  
 **Lib:** si la opción del compilador “wchar\_t es tipo nativo” está activada, use omsuppw.lib o comsuppwd.lib.  Si “wchar\_t es tipo nativo” está desactivada, use comsupp.lib.  Para obtener más información, vea [\/Zc:wchar\_t \(wchar\_t es un tipo nativo\)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).  
  
## Vea también  
 [Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)   
 [\_set\_com\_error\_handler](../cpp/set-com-error-handler.md)