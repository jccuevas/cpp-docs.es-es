---
title: Clase COleException
ms.date: 11/04/2016
f1_keywords:
- COleException
- AFXDISP/COleException
- AFXDISP/COleException::Process
- AFXDISP/COleException::m_sc
helpviewer_keywords:
- COleException [MFC], Process
- COleException [MFC], m_sc
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
ms.openlocfilehash: 737c9e669990f4de6ae18cdc7662c131ad61516f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375006"
---
# <a name="coleexception-class"></a>Clase COleException

Representa una condición de excepción relacionada con una operación OLE.

## <a name="syntax"></a>Sintaxis

```
class COleException : public CException
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleException::Process](#process)|Traduce una excepción detectada en un código de retorno OLE.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleException::m_sc](#m_sc)|Contiene el código de estado que indica el motivo de la excepción.|

## <a name="remarks"></a>Observaciones

La `COleException` clase incluye un miembro de datos públicos que contiene el código de estado que indica el motivo de la excepción.

En general, no debe `COleException` crear un objeto directamente; en su lugar, debe llamar a [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Para obtener más información sobre las excepciones, vea los artículos Control de excepciones [(MFC)](../../mfc/exception-handling-in-mfc.md) y [Excepciones: Excepciones OLE](../../mfc/exceptions-ole-exceptions.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="coleexceptionm_sc"></a><a name="m_sc"></a>COleException::m_sc

Este miembro de datos contiene el código de estado OLE que indica el motivo de la excepción.

```
SCODE m_sc;
```

### <a name="remarks"></a>Observaciones

El valor de esta variable se establece mediante [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Para obtener más información sobre SCODE, vea [Estructura de códigos de error COM](/windows/win32/com/structure-of-com-error-codes) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

## <a name="coleexceptionprocess"></a><a name="process"></a>COleException::Process

Llame a la **Process** función miembro para traducir una excepción detectada en un código de estado OLE.

```
static SCODE PASCAL Process(const CException* pAnyException);
```

### <a name="parameters"></a>Parámetros

*pAnyException*<br/>
Puntero a una excepción detectada.

### <a name="return-value"></a>Valor devuelto

Un código de estado OLE.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Esta función es **estática.**

Para obtener más información sobre SCODE, vea [Estructura de códigos de error COM](/windows/win32/com/structure-of-com-error-codes) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Clase CException](../../mfc/reference/cexception-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
