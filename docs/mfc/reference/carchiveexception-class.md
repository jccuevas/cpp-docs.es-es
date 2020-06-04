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
ms.openlocfilehash: ad2a9d8c5b4466a04b5a88fcce7679911bf1b81a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377013"
---
# <a name="carchiveexception-class"></a>Clase CArchiveException

Representa una condición de excepción de serialización

## <a name="syntax"></a>Sintaxis

```
class CArchiveException : public CException
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CArchiveException::CArchiveException](#carchiveexception)|Construye un objeto `CArchiveException`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CArchiveException::m_cause](#m_cause)|Indica la causa de la excepción.|
|[CArchiveException::m_strFileName](#m_strfilename)|Especifica el nombre del archivo para esta condición de excepción.|

## <a name="remarks"></a>Observaciones

La `CArchiveException` clase incluye un miembro de datos públicos que indica la causa de la excepción.

`CArchiveException`objetos se construyen y se producen dentro de [CArchive](../../mfc/reference/carchive-class.md) funciones miembro. Puede tener acceso a estos objetos dentro del ámbito de una expresión **CATCH.** El código de causa es independiente del sistema operativo. Para obtener más información sobre el procesamiento de excepciones, vea Control de [excepciones (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="carchiveexceptioncarchiveexception"></a><a name="carchiveexception"></a>CArchiveException::CArchiveException

Construye un `CArchiveException` objeto, almacenando el valor de *causa* en el objeto.

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parámetros

*Causa*<br/>
Una variable de tipo enumerada que indica el motivo de la excepción. Para obtener una lista de los enumeradores, vea el [m_cause](#m_cause) miembro de datos.

*lpszArchiveName*<br/>
Apunta a una cadena que `CArchive` contiene el nombre del objeto que causa la excepción.

### <a name="remarks"></a>Observaciones

Puede crear `CArchiveException` un objeto en el montón y lanzarlo usted mismo o dejar que la función global [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) lo controle por usted.

No utilice este constructor directamente; en su lugar, `AfxThrowArchiveException`llame a la función global .

## <a name="carchiveexceptionm_cause"></a><a name="m_cause"></a>CArchiveException::m_cause

Especifica la causa de la excepción.

```
int m_cause;
```

### <a name="remarks"></a>Observaciones

Este miembro de datos es una variable pública de tipo **int**. Sus valores se `CArchiveException` definen mediante un tipo enumerado. A continuación se indican los enumeradores y el significado de cada uno de ellos:

- `CArchiveException::none`No se ha producido ningún error.

- `CArchiveException::genericException`Error no especificado.

- `CArchiveException::readOnly`Intentó escribir en un archivo abierto para cargarlo.

- `CArchiveException::endOfFile`Se ha alcanzado el final del archivo mientras se lee un objeto.

- `CArchiveException::writeOnly`Intentó leer desde un archivo abierto para almacenar.

- `CArchiveException::badIndex`Formato de archivo no válido.

- `CArchiveException::badClass`Intentó leer un objeto en un objeto del tipo incorrecto.

- `CArchiveException::badSchema`Intentó leer un objeto con una versión diferente de la clase.

    > [!NOTE]
    >  Estos enumeradores de causa de `CArchiveException` son distintos de los enumeradores de causa de `CFileException`.

    > [!NOTE]
    > `CArchiveException::generic` está desusada. En su lugar, use `genericException`. Si se utiliza **genérico** en una aplicación y se compila con /clr, habrá errores de sintaxis que no son fáciles de descifrar.

## <a name="carchiveexceptionm_strfilename"></a><a name="m_strfilename"></a>CArchiveException::m_strFileName

Especifica el nombre del archivo para esta condición de excepción.

```
CString m_strFileName;
```

## <a name="see-also"></a>Consulte también

[Clase CException](../../mfc/reference/cexception-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CArchive (clase)](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[Procesamiento de excepciones](../../mfc/reference/exception-processing.md)
