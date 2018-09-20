---
title: CFixedStringT (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
dev_langs:
- C++
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6ac44a9a27b5c3ad62279dc3065aa9e0aac5236
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378233"
---
# <a name="cfixedstringt-class"></a>CFixedStringT (clase)

Esta clase representa un objeto de cadena con un búfer de caracteres fijos.

## <a name="syntax"></a>Sintaxis

```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```

#### <a name="parameters"></a>Parámetros

*StringType*  
Usa como clase base para el objeto de cadena fija y puede ser cualquier `CStringT`-tipo basado en. Algunos ejemplos incluyen `CString`, `CStringA`, y `CStringW`.

*t_nChars*  
El número de caracteres almacenados en el búfer.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CFixedStringT::CFixedStringT](#cfixedstringt)|El constructor para el objeto de cadena.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CFixedStringT::operator =](#eq)|Asigna un nuevo valor a un `CFixedStringT` objeto.|

## <a name="remarks"></a>Comentarios

Esta clase es un ejemplo de una clase de cadena personalizada basada en `CStringT`. Aunque es bastante similar, las dos clases se diferencian en la implementación. Las principales diferencias entre `CFixedStringT` y `CStringT` son:

- El búfer del carácter inicial se asigna como parte del objeto y tiene un tamaño *t_nChars*. Esto permite la `CFixedString` objeto ocupando un fragmento de memoria contigua para mejorar el rendimiento. Sin embargo, si el contenido de un `CFixedStringT` supere el objeto *t_nChars*, el búfer se asigna dinámicamente.

- El búfer de caracteres para un `CFixedStringT` objeto siempre es la misma longitud ( *t_nChars*). No hay ninguna limitación de tamaño de búfer para `CStringT` objetos.

- El Administrador de memoria para `CFixedStringT` se personaliza de forma que el uso compartido de un [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md) objeto entre dos o más `CFixedStringT` objectsis no permitido. `CStringT` objetos no tienen esta limitación.

Para obtener más información sobre la personalización de `CFixedStringT` y administración de memoria para objetos de cadena en general, vea [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IAtlStringMgr`

`StringType`

`CFixedStringMgr`

`CFixedStringT`

## <a name="requirements"></a>Requisitos

**Encabezado:** cstringt.h

##  <a name="cfixedstringt"></a>  CFixedStringT::CFixedStringT

Construye un objeto `CFixedStringT`.

```
CFixedStringT() throw();
explicit CFixedStringT(IAtlStringMgr* pStringMgr) throw();
CFixedStringT(const CFixedStringT<StringType, t_nChars>& str);
CFixedStringT(const StringType& str);
CFixedStringT(const StringType::XCHAR* psz);
explicit CFixedStringT(const StringType::YCHAR* psz);
explicit CFixedStringT(const unsigned char* psz);
```

### <a name="parameters"></a>Parámetros

*psz*  
Una cadena terminada en null que se copiará en esto `CFixedStringT` objeto.

*str*  
Existente `CFixedStringT` objeto que se copiará en esto `CFixedStringT` objeto.

*pStringMgr*  
Un puntero para el Administrador de memoria de la `CFixedStringT` objeto. Para obtener más información sobre `IAtlStringMgr` y administración de memoria para `CFixedStringT`, consulte [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

### <a name="remarks"></a>Comentarios

Dado que los constructores copian los datos de entrada en el nuevo almacenamiento asignado, debe tener en cuenta que pueden dar lugar a excepciones de memoria. Tenga en cuenta que algunos de estos constructores actúan como funciones de conversión.

##  <a name="operator__eq"></a>  CFixedStringT::operator =

Reinicializa un existente `CFixedStringT` objeto con datos nuevos.

```
CFixedStringT<StringType, t_nChars>& operator=(
    const CFixedStringT<StringType, t_nChars>& str);
CFixedStringT<StringType, t_nChars>& operator=(const char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* psz);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& str);
```

### <a name="parameters"></a>Parámetros

*str*  
Una cadena terminada en null que se copiará en esto `CFixedStringT` objeto.

*psz*  
Existente `CFixedStringT` que se copiará en esto `CFixedStringT` objeto.

### <a name="remarks"></a>Comentarios

Debe tener en cuenta que pueden producirse excepciones siempre que use el operador de asignación, porque a menudo se asigna nuevo almacenamiento para almacenar el resultado de la memoria `CFixedStringT` objeto.

## <a name="see-also"></a>Vea también

[CStringT (clase)](../../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas ATL y MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)

