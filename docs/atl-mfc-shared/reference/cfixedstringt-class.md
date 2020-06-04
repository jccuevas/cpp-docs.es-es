---
title: CFixedStringT (Clase)
ms.date: 03/27/2019
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
ms.openlocfilehash: fe096185f6f0b71ad45757cd0b75ab13c41e5f5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317827"
---
# <a name="cfixedstringt-class"></a>CFixedStringT (Clase)

Esta clase representa un objeto de cadena con un búfer de caracteres fijo.

## <a name="syntax"></a>Sintaxis

```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```

#### <a name="parameters"></a>Parámetros

*StringType*<br/>
Se utiliza como la clase base para `CStringT`el objeto de cadena fija y puede ser cualquier tipo basado en . Algunos ejemplos `CString` `CStringA`incluyen `CStringW`, , y .

*t_nChars*<br/>
El número de caracteres almacenados en el búfer.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFixedStringT::CFixedStringT](#cfixedstringt)|El constructor del objeto de cadena.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFixedStringT::operator ?](#operator_eq)|Asigna un nuevo valor `CFixedStringT` a un objeto.|

## <a name="remarks"></a>Observaciones

Esta clase es un ejemplo de `CStringT`una clase de cadena personalizada basada en . Aunque similar, las dos clases difieren en la implementación. Las principales diferencias entre `CFixedStringT` y `CStringT` son:

- El búfer de caracteres inicial se asigna como parte del objeto y tiene el tamaño *t_nChars*. Esto permite `CFixedString` que el objeto ocupe un fragmento de memoria contiguo para fines de rendimiento. Sin embargo, si `CFixedStringT` el contenido de un objeto crece más allá *de t_nChars*, el búfer se asigna dinámicamente.

- El búfer de `CFixedStringT` caracteres de un objeto siempre tiene la misma longitud ( *t_nChars*). No hay ninguna limitación `CStringT` en el tamaño del búfer para los objetos.

- El administrador `CFixedStringT` de memoria para se personaliza de modo que `CFixedStringT` no se permite el uso compartido de un [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md) objeto entre dos o más objetos. `CStringT`objetos no tienen esta limitación.

Para obtener más información `CFixedStringT` sobre la personalización y la administración de memoria para objetos de cadena en general, vea Administración de [memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IAtlStringMgr`

`StringType`

`CFixedStringMgr`

`CFixedStringT`

## <a name="requirements"></a>Requisitos

**Encabezado:** cstringt.h

## <a name="cfixedstringtcfixedstringt"></a><a name="cfixedstringt"></a>CFixedStringT::CFixedStringT

Construye un objeto `CFixedStringT`.

```
CFixedStringT() throw();
explicit CFixedStringT(IAtlStringMgr* pStringMgr) throw();
CFixedStringT(const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT(const StringType& strSrc);
CFixedStringT(const StringType::XCHAR* pszSrc);
explicit CFixedStringT(const StringType::YCHAR* pszSrc);
explicit CFixedStringT(const unsigned char* pszSrc);
```

### <a name="parameters"></a>Parámetros

*pszSrc*<br/>
Cadena terminada en null que se `CFixedStringT` va a copiar en este objeto.

*strSrc*<br/>
Objeto `CFixedStringT` existente que se va `CFixedStringT` a copiar en este objeto.

*pStringMgr*<br/>
Un puntero al administrador `CFixedStringT` de memoria del objeto. Para obtener `IAtlStringMgr` más información `CFixedStringT`sobre la administración de memoria y la administración de memoria para , vea Administración de [memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

### <a name="remarks"></a>Observaciones

Dado que los constructores copian los datos de entrada en el nuevo almacenamiento asignado, debe tener en cuenta que pueden producirse excepciones de memoria. Algunos de estos constructores actúan como funciones de conversión.

## <a name="cfixedstringtoperator-"></a><a name="operator_eq"></a>CFixedStringT::operator ?

Reinicializa un `CFixedStringT` objeto existente con nuevos datos.

```
CFixedStringT<StringType, t_nChars>& operator=(
    const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT<StringType, t_nChars>& operator=(const char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& strSrc);
```

### <a name="parameters"></a>Parámetros

*pszSrc*<br/>
Cadena terminada en null que se `CFixedStringT` va a copiar en este objeto.

*strSrc*<br/>
Una `CFixedStringT` existente que se `CFixedStringT` va a copiar en este objeto.

### <a name="remarks"></a>Observaciones

Debe tener en cuenta que pueden producirse excepciones de memoria siempre que `CFixedStringT` utilice el operador de asignación porque a menudo se asigna nuevo almacenamiento para contener el objeto resultante.

## <a name="see-also"></a>Consulte también

[Clase CStringT](../../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
