---
title: _com_error (Clase)
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: 0c33791fbe6011a3eddc6e535a3a4ed838e5e06c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180815"
---
# <a name="_com_error-class"></a>_com_error (Clase)

**Específicos de Microsoft**

Un objeto **_com_error** representa una condición de excepción detectada por las funciones contenedoras de control de errores en los archivos de encabezado generados a partir de la biblioteca de tipos o mediante una de las clases de compatibilidad con com. La clase **_com_error** encapsula el código de error HRESULT y cualquier objeto `IErrorInfo Interface` asociado.

### <a name="construction"></a>Construcción

|||
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|Construye un objeto de **_com_error** .|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador =](../cpp/com-error-operator-equal.md)|Asigna un objeto de **_com_error** existente a otro.|

### <a name="extractor-functions"></a>Funciones de extractor

|||
|-|-|
|[Error](../cpp/com-error-error.md)|Recupera el HRESULT que se pasa al constructor.|
|[ErrorInfo](../cpp/com-error-errorinfo.md)|Recupera el objeto `IErrorInfo` pasado al constructor.|
|[WCode](../cpp/com-error-wcode.md)|Recupera el código de error de 16 bits asignado al HRESULT encapsulado.|

### <a name="ierrorinfo-functions"></a>Funciones de IErrorInfo

|||
|-|-|
|[Descripción](../cpp/com-error-description.md)|Llama a la función `IErrorInfo::GetDescription`.|
|[HelpContext](../cpp/com-error-helpcontext.md)|Llama a la función `IErrorInfo::GetHelpContext`.|
|[HelpFile](../cpp/com-error-helpfile.md)|Llama a la función `IErrorInfo::GetHelpFile`.|
|[Origen](../cpp/com-error-source.md)|Llama a la función `IErrorInfo::GetSource`.|
|[GUID](../cpp/com-error-guid.md)|Llama a la función `IErrorInfo::GetGUID`.|

### <a name="format-message-extractor"></a>Extractor de mensajes de formato

|||
|-|-|
|[ErrorMessage](../cpp/com-error-errormessage.md)|Recupera el mensaje de cadena para HRESULT almacenado en el objeto **_com_error** .|

### <a name="exepinfowcode-to-hresult-mappers"></a>Asignadores de ExepInfo.wCode a HRESULT

|||
|-|-|
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|Asigna HRESULT de 32 bits a `wCode`de 16 bits.|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Asigna `wCode` de 16 bits al HRESULT de 32 bits.|

**FIN de Específicos de Microsoft**

## <a name="requirements"></a>Requisitos

**Encabezado:** \<comdef. h >

`Lib:` omsuppw. lib o comsuppwd. lib (vea [/Zc: wchar_t (Wchar_t es un tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obtener más información)

## <a name="see-also"></a>Consulte también

[Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)<br/>
[IErrorInfo (interfaz)](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)
