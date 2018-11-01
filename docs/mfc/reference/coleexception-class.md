---
title: COleException (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleException
- AFXDISP/COleException
- AFXDISP/COleException::Process
- AFXDISP/COleException::m_sc
dev_langs:
- C++
helpviewer_keywords:
- COleException [MFC], Process
- COleException [MFC], m_sc
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2705a1889e7b9c9c0960cce45b8dc7b411e16982
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061007"
---
# <a name="coleexception-class"></a>COleException (clase)

Representa una condición de excepción relacionada con una operación OLE.

## <a name="syntax"></a>Sintaxis

```
class COleException : public CException
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleException::Process](#process)|Convierte una excepción detectada en un código de retorno OLE.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[COleException::m_sc](#m_sc)|Contiene el código de estado que indica el motivo de la excepción.|

## <a name="remarks"></a>Comentarios

La `COleException` clase incluye un miembro de datos públicos que contiene el código de estado que indica el motivo de la excepción.

En general, no debería crear un `COleException` objeto directamente; en su lugar, debe llamar a [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Para obtener más información sobre las excepciones, consulte los artículos [de control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md) y [excepciones: excepciones OLE](../../mfc/exceptions-ole-exceptions.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

##  <a name="m_sc"></a>  COleException::m_sc

Este miembro de datos contiene el código de estado OLE que indica el motivo de la excepción.

```
SCODE m_sc;
```

### <a name="remarks"></a>Comentarios

Valor de la variable se establece [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Para obtener más información sobre SCODE, consulte [estructura de códigos de Error COM](/windows/desktop/com/structure-of-com-error-codes) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

##  <a name="process"></a>  COleException::Process

Llame a la **proceso** función miembro para convertir una excepción detectada en un código de estado OLE.

```
static SCODE PASCAL Process(const CException* pAnyException);
```

### <a name="parameters"></a>Parámetros

*pAnyException*<br/>
Puntero a una excepción detectada.

### <a name="return-value"></a>Valor devuelto

Un código de estado OLE.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Esta función es **estático**.

Para obtener más información sobre SCODE, consulte [estructura de códigos de Error COM](/windows/desktop/com/structure-of-com-error-codes) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CALCDRIV](../../visual-cpp-samples.md)<br/>
[CException (clase)](../../mfc/reference/cexception-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)

