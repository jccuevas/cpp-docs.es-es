---
title: Clase CArchiveException
ms.date: 11/04/2016
f1_keywords:
- CArchiveException
- AFX/CArchiveException
- AFX/CArchiveException::CArchiveException
- AFX/CArchiveException::m_cause
- AFX/CArchiveException::m_strFileName
helpviewer_keywords:
- CArchiveException [MFC], CArchiveException
- CArchiveException [MFC], m_cause
- CArchiveException [MFC], m_strFileName
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
ms.openlocfilehash: 731735bccf9225e67d82b1fe90336c92a630b368
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426112"
---
# <a name="carchiveexception-class"></a>Clase CArchiveException

Representa una condición de excepción de serialización.

## <a name="syntax"></a>Sintaxis

```
class CArchiveException : public CException
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CArchiveException::CArchiveException](#carchiveexception)|Construye un objeto `CArchiveException`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CArchiveException:: m_cause](#m_cause)|Indica la causa de la excepción.|
|[CArchiveException:: m_strFileName](#m_strfilename)|Especifica el nombre del archivo para esta condición de excepción.|

## <a name="remarks"></a>Observaciones

La clase `CArchiveException` incluye un miembro de datos público que indica la causa de la excepción.

`CArchiveException` objetos se construyen y se inician dentro de las funciones miembro de [CArchive](../../mfc/reference/carchive-class.md) . Puede tener acceso a estos objetos dentro del ámbito de una expresión **catch** . El código de causa es independiente del sistema operativo. Para obtener más información sobre el procesamiento de excepciones, vea [control de excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException (](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="carchiveexception"></a>CArchiveException::CArchiveException

Construye un objeto `CArchiveException`, almacenando el valor de *causa* en el objeto.

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parámetros

*cause*<br/>
Variable de tipo enumerado que indica la razón de la excepción. Para obtener una lista de los enumeradores, vea el [m_cause](#m_cause) miembro de datos.

*lpszArchiveName*<br/>
Apunta a una cadena que contiene el nombre del objeto `CArchive` que produce la excepción.

### <a name="remarks"></a>Observaciones

Puede crear un objeto de `CArchiveException` en el montón y producirlo usted mismo o dejar que la función global [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) lo controle automáticamente.

No utilice este constructor directamente; en su lugar, llame a la función global `AfxThrowArchiveException`.

##  <a name="m_cause"></a>CArchiveException:: m_cause

Especifica la causa de la excepción.

```
int m_cause;
```

### <a name="remarks"></a>Observaciones

Este miembro de datos es una variable pública de tipo **int**. Sus valores se definen mediante un `CArchiveException` tipo enumerado. A continuación se indican los enumeradores y el significado de cada uno de ellos:

- `CArchiveException::none` no se ha producido ningún error.

- `CArchiveException::genericException` error no especificado.

- `CArchiveException::readOnly` intentó escribir en un archivo abierto para cargarse.

- `CArchiveException::endOfFile` alcanzó el final del archivo al leer un objeto.

- `CArchiveException::writeOnly` intentó leer desde un archivo abierto para almacenar.

- `CArchiveException::badIndex` formato de archivo no válido.

- `CArchiveException::badClass` intentó leer un objeto en un objeto del tipo incorrecto.

- `CArchiveException::badSchema` intentó leer un objeto con una versión diferente de la clase.

    > [!NOTE]
    >  Estos enumeradores de causa de `CArchiveException` son distintos de los enumeradores de causa de `CFileException`.

    > [!NOTE]
    > `CArchiveException::generic` está desusada. En su lugar, use `genericException`. Si se usa **Generic** en una aplicación y se compila con/CLR, habrá errores de sintaxis que no son fáciles de descifrar.

##  <a name="m_strfilename"></a>CArchiveException:: m_strFileName

Especifica el nombre del archivo para esta condición de excepción.

```
CString m_strFileName;
```

## <a name="see-also"></a>Consulte también

[CException (clase)](../../mfc/reference/cexception-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CArchive (clase)](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[Procesamiento de excepciones](../../mfc/reference/exception-processing.md)
