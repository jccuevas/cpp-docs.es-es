---
title: "_com_error (Clase) | Microsoft Docs"
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
  - "_com_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_com_error (clase)"
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Un objeto `_com_error` representa una condición de excepción detectada por las funciones contenedoras de control de errores en los archivos de encabezado generados a partir de la biblioteca de tipos o por una de las clases de soporte de COM.  La clase `_com_error` encapsula el código de error `HRESULT` y cualquier objeto `IErrorInfo Interface` asociado.  
  
### Construcción  
  
|||  
|-|-|  
|[\_com\_error](../cpp/com-error-com-error.md)|Construye un objeto `_com_error`.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../cpp/com-error-operator-equal.md)|Asigna un objeto `_com_error` existente a otro.|  
  
### Funciones de extractor  
  
|||  
|-|-|  
|[Error](../cpp/com-error-error.md)|Recupera el `HRESULT` pasado al constructor.|  
|[ErrorInfo](../cpp/com-error-errorinfo.md)|Recupera el objeto `IErrorInfo` pasado al constructor.|  
|[WCode](../cpp/com-error-wcode.md)|Recupera el código de error de 16 bits asignado en el `HRESULT`encapsulado.|  
  
### Funciones de IErrorInfo  
  
|||  
|-|-|  
|[Descripción](../cpp/com-error-description.md)|Llama a la función `IErrorInfo::GetDescription`.|  
|[HelpContext](../cpp/com-error-helpcontext.md)|Llama a la función `IErrorInfo::GetHelpContext`.|  
|[HelpFile](../cpp/com-error-helpfile.md)|Llama a la función `IErrorInfo::GetHelpFile`.|  
|[Origen](../cpp/com-error-source.md)|Llama a la función `IErrorInfo::GetSource`.|  
|[GUID](../cpp/com-error-guid.md)|Llama a la función `IErrorInfo::GetGUID`.|  
  
### Extractor de mensajes de formato  
  
|||  
|-|-|  
|[ErrorMessage](../cpp/com-error-errormessage.md)|Recupera el mensaje de cadena para HRESULT almacenado en el objeto `_com_error`.|  
  
### Asignadores de ExepInfo.wCode a HRESULT  
  
|||  
|-|-|  
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|Asigna un `HRESULT` de 32 bits a un `wCode` de 16 bits.|  
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Asigna un `wCode` de 16 bits a un `HRESULT` de 32 bits.|  
  
## Específicos de Microsoft: END  
  
## Requisitos  
 `Header:` comdef.h  
  
 `Lib:` comsuppw.lib o comsuppwd.lib \(vea [\/Zc:wchar\_t \(wchar\_t es un tipo nativo\)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obtener más información\)  
  
## Vea también  
 [Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)   
 [IErrorInfo Interface](http://msdn.microsoft.com/es-es/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)