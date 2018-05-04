---
title: CFixedStringT (clase) | Documentos de Microsoft
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
ms.openlocfilehash: 93125d15be32a95d71c763f476fad700dab65a3b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="cfixedstringt-class"></a>CFixedStringT (clase)
Esta clase representa un objeto de cadena con un búfer de caracteres fijas.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```  
  
#### <a name="parameters"></a>Parámetros  
 `StringType`  
 Usar como clase base para el objeto de cadena fija y puede ser cualquier `CStringT`-según el tipo. Algunos ejemplos son `CString`, `CStringA`, y `CStringW`.  
  
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
 Esta clase es un ejemplo de una clase de cadena personalizada basada en `CStringT`. Aunque es muy similar, se diferencian las dos clases en implementación. Las principales diferencias entre `CFixedStringT` y `CStringT` son:  
  
-   El búfer de carácter inicial se asigna como parte del objeto y tiene un tamaño *t_nChars*. Esto permite la **CFixedString** objeto para ocupar un bloque de memoria contigua para optimizar el rendimiento. Sin embargo, si el contenido de un `CFixedStringT` objeto exceda *t_nChars*, el búfer se asigna dinámicamente.  
  
-   El búfer de caracteres para un `CFixedStringT` objeto siempre tiene la misma longitud ( *t_nChars*). No hay ninguna limitación de tamaño de búfer para `CStringT` objetos.  
  
-   El Administrador de memoria para `CFixedStringT` personalizado que el uso compartido de un [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md) objeto entre dos o más `CFixedStringT` objectsis no permitido. `CStringT` objetos no tienen esta limitación.  
  
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
 `psz`  
 Una cadena terminada en null que se copiará en esto `CFixedStringT` objeto.  
  
 `str`  
 Existente `CFixedStringT` objeto que se copiará en esto `CFixedStringT` objeto.  
  
 `pStringMgr`  
 Un puntero al administrador de memoria de la `CFixedStringT` objeto. Para obtener más información sobre `IAtlStringMgr` y administración de memoria para `CFixedStringT`, consulte [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
### <a name="remarks"></a>Comentarios  
 Puesto que los constructores copian los datos de entrada en el nuevo almacenamiento asignado, debe tener en cuenta que pueden dar lugar a excepciones de la memoria. Tenga en cuenta que algunos de estos constructores actúen como funciones de conversión.  
  
##  <a name="operator__eq"></a>  CFixedStringT::operator =  
 Reinicializa existente `CFixedStringT` objeto con datos nuevos.  
  
```
CFixedStringT<StringType, t_nChars>& operator=(
  const CFixedStringT<StringType, t_nChars>& str);
CFixedStringT<StringType, t_nChars>& operator=(const char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* psz);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& str);
```  
  
### <a name="parameters"></a>Parámetros  
 `str`  
 Una cadena terminada en null que se copiará en esto `CFixedStringT` objeto.  
  
 `psz`  
 Existente `CFixedStringT` que se copiará en esto `CFixedStringT` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Debe tener en cuenta que la memoria pueden producir excepciones siempre que se use el operador de asignación porque a menudo se asigna nuevo almacenamiento para contener resultante `CFixedStringT` objeto.  
  
## <a name="see-also"></a>Vea también  
 [CStringT (clase)](../../atl-mfc-shared/reference/cstringt-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases compartidas de ATL y MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)




