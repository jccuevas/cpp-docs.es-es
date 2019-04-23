---
title: COleDispatchException (clase)
ms.date: 11/04/2016
f1_keywords:
- COleDispatchException
- AFXDISP/COleDispatchException
- AFXDISP/COleDispatchException::m_dwHelpContext
- AFXDISP/COleDispatchException::m_strDescription
- AFXDISP/COleDispatchException::m_strHelpFile
- AFXDISP/COleDispatchException::m_strSource
- AFXDISP/COleDispatchException::m_wCode
helpviewer_keywords:
- COleDispatchException [MFC], m_dwHelpContext
- COleDispatchException [MFC], m_strDescription
- COleDispatchException [MFC], m_strHelpFile
- COleDispatchException [MFC], m_strSource
- COleDispatchException [MFC], m_wCode
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
ms.openlocfilehash: 2d5b9d2a0dc1e716ea8cb20f0d0dcb4c5d765079
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58769061"
---
# <a name="coledispatchexception-class"></a>COleDispatchException (clase)

Controla las excepciones específicas de la interfaz OLE de `IDispatch` , que es una parte fundamental de la automatización OLE.

## <a name="syntax"></a>Sintaxis

```
class COleDispatchException : public CException
```

## <a name="members"></a>Miembros

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[COleDispatchException::m_dwHelpContext](#m_dwhelpcontext)|Contexto de ayuda para el error.|
|[COleDispatchException::m_strDescription](#m_strdescription)|Descripción del error.|
|[COleDispatchException::m_strHelpFile](#m_strhelpfile)|Archivo de ayuda para usar con `m_dwHelpContext`.|
|[COleDispatchException::m_strSource](#m_strsource)|Aplicación que generó la excepción.|
|[COleDispatchException::m_wCode](#m_wcode)|`IDispatch`-código de error específico.|

## <a name="remarks"></a>Comentarios

Como las demás clases de excepción derivan de la `CException` de la clase base `COleDispatchException` puede utilizarse con las macros THROW, THROW_LAST, TRY, CATCH, AND_CATCH y END_CATCH.

En general, debe llamar a [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) para crear y producir un `COleDispatchException` objeto.

Para obtener más información sobre las excepciones, consulte los artículos [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md) y [excepciones: Excepciones OLE](../../mfc/exceptions-ole-exceptions.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleDispatchException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

##  <a name="m_dwhelpcontext"></a>  COleDispatchException::m_dwHelpContext

Identifica un contexto de ayuda en la Ayuda de la aplicación (. Archivo HLP).

```
DWORD m_dwHelpContext;
```

### <a name="remarks"></a>Comentarios

Este miembro se establece mediante la función [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) cuando se produce una excepción.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

##  <a name="m_strdescription"></a>  COleDispatchException::m_strDescription

Contiene una descripción del error, como "Disco lleno".

```
CString m_strDescription;
```

### <a name="remarks"></a>Comentarios

Este miembro se establece mediante la función [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) cuando se produce una excepción.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

##  <a name="m_strhelpfile"></a>  COleDispatchException::m_strHelpFile

El marco de trabajo se rellena de esta cadena con el nombre del archivo de Ayuda de la aplicación.

```
CString m_strHelpFile;
```

##  <a name="m_strsource"></a>  COleDispatchException::m_strSource

El marco de trabajo se rellena de esta cadena con el nombre de la aplicación que generó la excepción.

```
CString m_strSource;
```

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

##  <a name="m_wcode"></a>  COleDispatchException::m_wCode

Contiene un código de error específico para su aplicación.

```
WORD m_wCode;
```

### <a name="remarks"></a>Comentarios

Este miembro se establece mediante la función [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) cuando se produce una excepción.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[CException (clase)](../../mfc/reference/cexception-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDispatchDriver (clase)](../../mfc/reference/coledispatchdriver-class.md)<br/>
[COleException (clase)](../../mfc/reference/coleexception-class.md)
