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
ms.openlocfilehash: 4572b639b757569d8e3cfa731f99c123762f3900
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375061"
---
# <a name="coledispatchexception-class"></a>COleDispatchException (clase)

Controla las excepciones específicas de la interfaz OLE de `IDispatch` , que es una parte fundamental de la automatización OLE.

## <a name="syntax"></a>Sintaxis

```
class COleDispatchException : public CException
```

## <a name="members"></a>Miembros

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDispatchException::m_dwHelpContext](#m_dwhelpcontext)|Contexto de ayuda para el error.|
|[COleDispatchException::m_strDescription](#m_strdescription)|Descripción del error verbal.|
|[COleDispatchException::m_strHelpFile](#m_strhelpfile)|Archivo de ayuda `m_dwHelpContext`para usar con .|
|[COleDispatchException::m_strSource](#m_strsource)|Aplicación que generó la excepción.|
|[COleDispatchException::m_wCode](#m_wcode)|`IDispatch`-código de error específico.|

## <a name="remarks"></a>Observaciones

Al igual que las otras `CException` clases `COleDispatchException` de excepción derivadas de la clase base, se pueden utilizar con las macros THROW, THROW_LAST, TRY, CATCH, AND_CATCH y END_CATCH.

En general, debe llamar a [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) para crear y producir un `COleDispatchException` objeto.

Para obtener más información sobre las excepciones, vea los artículos Control de excepciones [(MFC)](../../mfc/exception-handling-in-mfc.md) y [Excepciones: Excepciones OLE](../../mfc/exceptions-ole-exceptions.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleDispatchException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="coledispatchexceptionm_dwhelpcontext"></a><a name="m_dwhelpcontext"></a>COleDispatchException::m_dwHelpContext

Identifica un contexto de ayuda en la ayuda de la aplicación (. HLP).

```
DWORD m_dwHelpContext;
```

### <a name="remarks"></a>Observaciones

Este miembro se establece mediante la función [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) cuando se produce una excepción.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="coledispatchexceptionm_strdescription"></a><a name="m_strdescription"></a>COleDispatchException::m_strDescription

Contiene una descripción de error verbal, como "Disco lleno."

```
CString m_strDescription;
```

### <a name="remarks"></a>Observaciones

Este miembro se establece mediante la función [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) cuando se produce una excepción.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="coledispatchexceptionm_strhelpfile"></a><a name="m_strhelpfile"></a>COleDispatchException::m_strHelpFile

El marco de trabajo rellena esta cadena con el nombre del archivo de ayuda de la aplicación.

```
CString m_strHelpFile;
```

## <a name="coledispatchexceptionm_strsource"></a><a name="m_strsource"></a>COleDispatchException::m_strSource

El marco de trabajo rellena esta cadena con el nombre de la aplicación que generó la excepción.

```
CString m_strSource;
```

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="coledispatchexceptionm_wcode"></a><a name="m_wcode"></a>COleDispatchException::m_wCode

Contiene un código de error específico de la aplicación.

```
WORD m_wCode;
```

### <a name="remarks"></a>Observaciones

Este miembro se establece mediante la función [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) cuando se produce una excepción.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Clase CException](../../mfc/reference/cexception-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)<br/>
[Clase COleException](../../mfc/reference/coleexception-class.md)
