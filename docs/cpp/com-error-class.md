---
title: _com_error Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error
dev_langs:
- C++
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 53defbe6c686630791317fa20aca48414144eb91
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="comerror-class"></a>_com_error (Clase)
**Específicos de Microsoft**  
  
 Un objeto `_com_error` representa una condición de excepción detectada por las funciones contenedoras de control de errores en los archivos de encabezado generados a partir de la biblioteca de tipos o por una de las clases de soporte de COM. La clase `_com_error` encapsula el código de error `HRESULT` y cualquier objeto `IErrorInfo Interface` asociado.  
  
### <a name="construction"></a>Construcción  
  
|||  
|-|-|  
|[_com_error](../cpp/com-error-com-error.md)|Construye un objeto `_com_error`.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador =](../cpp/com-error-operator-equal.md)|Asigna un objeto `_com_error` existente a otro.|  
  
### <a name="extractor-functions"></a>Funciones de extractor  
  
|||  
|-|-|  
|[Error](../cpp/com-error-error.md)|Recupera el `HRESULT` pasado al constructor.|  
|[ErrorInfo](../cpp/com-error-errorinfo.md)|Recupera el objeto `IErrorInfo` pasado al constructor.|  
|[WCode](../cpp/com-error-wcode.md)|Recupera el código de error de 16 bits asignado en el `HRESULT`encapsulado.|  
  
### <a name="ierrorinfo-functions"></a>Funciones de IErrorInfo  
  
|||  
|-|-|  
|[Descripción](../cpp/com-error-description.md)|Llama a la función `IErrorInfo::GetDescription`.|  
|[HelpContext](../cpp/com-error-helpcontext.md)|Llama a la función `IErrorInfo::GetHelpContext`.|  
|[HelpFile](../cpp/com-error-helpfile.md)|Llama a la función `IErrorInfo::GetHelpFile`.|  
|[Source](../cpp/com-error-source.md)|Llama a la función `IErrorInfo::GetSource`.|  
|[GUID](../cpp/com-error-guid.md)|Llama a la función `IErrorInfo::GetGUID`.|  
  
### <a name="format-message-extractor"></a>Extractor de mensajes de formato  
  
|||  
|-|-|  
|[ErrorMessage](../cpp/com-error-errormessage.md)|Recupera el mensaje de cadena para HRESULT almacenado en el objeto `_com_error`.|  
  
### <a name="exepinfowcode-to-hresult-mappers"></a>Asignadores de ExepInfo.wCode a HRESULT  
  
|||  
|-|-|  
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|Asigna un `HRESULT` de 32 bits a un `wCode` de 16 bits.|  
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Mapas de bits de 16 `wCode` a 32 bits `HRESULT`.|  
  
**FIN de Específicos de Microsoft**  
  
## <a name="requirements"></a>Requisitos  
 **Header:** \<comdef.h>  
  
 `Lib:`omsuppw.lib o comsuppwd.lib (vea [/Zc: wchar_t (wchar_t es tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obtener más información)  
  
## <a name="see-also"></a>Vea también  
 [Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)   
 [Interfaz IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)