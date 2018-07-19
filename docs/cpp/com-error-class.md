---
title: _com_error (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error
dev_langs:
- C++
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d59782b62ddfb51601505be6d12f01ce14cd4f1
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39026639"
---
# <a name="comerror-class"></a>_com_error (Clase)
**Específicos de Microsoft**  
  
 Un objeto `_com_error` representa una condición de excepción detectada por las funciones contenedoras de control de errores en los archivos de encabezado generados a partir de la biblioteca de tipos o por una de las clases de soporte de COM. El `_com_error` clase encapsula el código de error HRESULT y asociada ninguna `IErrorInfo Interface` objeto.  
  
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
|[Error](../cpp/com-error-error.md)|Recupera el valor HRESULT pasado al constructor.|  
|[ErrorInfo](../cpp/com-error-errorinfo.md)|Recupera el objeto `IErrorInfo` pasado al constructor.|  
|[WCode](../cpp/com-error-wcode.md)|Recupera el código de error de 16 bits asignado en el valor de HRESULT encapsulado.|  
  
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
|[Mensaje de error](../cpp/com-error-errormessage.md)|Recupera el mensaje de cadena para HRESULT almacenado en el objeto `_com_error`.|  
  
### <a name="exepinfowcode-to-hresult-mappers"></a>Asignadores de ExepInfo.wCode a HRESULT  
  
|||  
|-|-|  
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|Asigna el valor HRESULT de 32 bits a 16 bits `wCode`.|  
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Mapas de bits de 16 `wCode` HRESULT de 32 bits.|  
  
**FIN de Específicos de Microsoft**  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<comdef.h >  
  
 `Lib:` omsuppw.lib o comsuppwd.lib (vea [/Zc: wchar_t (wchar_t es tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obtener más información)  
  
## <a name="see-also"></a>Vea también  
 [Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)   
 [Interfaz IErrorInfo](http://msdn.microsoft.com/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)