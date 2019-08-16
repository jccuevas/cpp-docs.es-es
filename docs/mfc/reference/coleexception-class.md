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
ms.openlocfilehash: 96061f704d9df6cd788e362652b6ed22a7ffa999
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503948"
---
# <a name="coleexception-class"></a>Clase COleException

Representa una condición de excepción relacionada con una operación OLE.

## <a name="syntax"></a>Sintaxis

```
class COleException : public CException
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleException::Process](#process)|Convierte una excepción detectada en un código de retorno OLE.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleException::m_sc](#m_sc)|Contiene el código de estado que indica el motivo de la excepción.|

## <a name="remarks"></a>Comentarios

La `COleException` clase incluye un miembro de datos público que contiene el código de estado que indica el motivo de la excepción.

En general, no debe crear un `COleException` objeto directamente; en su lugar, debe llamar a [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Para obtener más información sobre excepciones, vea los artículos [control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md) y [excepciones: Excepciones](../../mfc/exceptions-ole-exceptions.md)OLE.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException (](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

##  <a name="m_sc"></a>  COleException::m_sc

Este miembro de datos contiene el código de estado OLE que indica la razón de la excepción.

```
SCODE m_sc;
```

### <a name="remarks"></a>Comentarios

El valor de esta variable se establece mediante [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Para obtener más información sobre SCODE, vea [estructura de los códigos de error com](/windows/win32/com/structure-of-com-error-codes) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

##  <a name="process"></a>COleException::P rador

Llame a la función miembro **Process** para convertir una excepción detectada en un código de estado OLE.

```
static SCODE PASCAL Process(const CException* pAnyException);
```

### <a name="parameters"></a>Parámetros

*pAnyException*<br/>
Puntero a una excepción detectada.

### <a name="return-value"></a>Valor devuelto

Un código de estado de OLE.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Esta función es **estática**.

Para obtener más información sobre SCODE, vea [estructura de los códigos de error com](/windows/win32/com/structure-of-com-error-codes) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[CException (clase)](../../mfc/reference/cexception-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
