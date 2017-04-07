---
title: CFixedStringT (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: f357a70a728b388c3b5d3d26ac4efd0d4c84434a
ms.lasthandoff: 02/24/2017

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
 Utiliza como clase base para el objeto de cadena fija y puede ser cualquier `CStringT`-según el tipo. Algunos ejemplos incluyen `CString`, `CStringA`, y `CStringW`.  
  
 *t_nChars*  
 El número de caracteres almacenados en el búfer.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFixedStringT::CFixedStringT](#cfixedstringt)|El constructor para el objeto de cadena.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFixedStringT::operator =](#eq)|Asigna un nuevo valor a un `CFixedStringT` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase es un ejemplo de una clase de cadena personalizada basada en `CStringT`. Aunque son bastante similares, se diferencian las dos clases de implementación. Las principales diferencias entre `CFixedStringT` y `CStringT` son:  
  
-   El búfer de carácter inicial se asigna como parte del objeto y tiene un tamaño *t_nChars*. Esto permite la **CFixedString** objeto ocupar un fragmento de memoria contigua para mejorar el rendimiento. Sin embargo, si el contenido de un `CFixedStringT` objeto crece más allá de *t_nChars*, el búfer se asigna dinámicamente.  
  
-   El búfer de caracteres para un `CFixedStringT` objeto siempre es la misma longitud ( *t_nChars*). No hay ninguna limitación de tamaño de búfer para `CStringT` objetos.  
  
-   El Administrador de memoria para `CFixedStringT` se personaliza tal que el uso compartido de un [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md) objeto entre dos o más `CFixedStringT` objectsis no permitido. `CStringT`objetos no tienen esta limitación.  
  
 Para obtener más información sobre la personalización de `CFixedStringT` y administración de memoria para objetos de cadena en general, vea [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IAtlStringMgr`  
  
 `StringType`  
  
 `CFixedStringMgr`  
  
 `CFixedStringT`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** cstringt.h  
  
##  <a name="cfixedstringt"></a>CFixedStringT::CFixedStringT  
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
 Una cadena terminada en null que se copiará en este `CFixedStringT` objeto.  
  
 `str`  
 Existente `CFixedStringT` el objeto que se copiará en este `CFixedStringT` objeto.  
  
 `pStringMgr`  
 Un puntero al administrador de memoria de la `CFixedStringT` objeto. Para obtener más información sobre `IAtlStringMgr` y administración de memoria para `CFixedStringT`, consulte [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
### <a name="remarks"></a>Comentarios  
 Dado que los constructores copian los datos de entrada en el nuevo almacenamiento asignado, debe tener en cuenta que la memoria pueden producir excepciones. Tenga en cuenta que algunos de estos constructores actúan como funciones de conversión.  
  
##  <a name="operator__eq"></a>CFixedStringT::operator =  
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
 Una cadena terminada en null que se copiará en este `CFixedStringT` objeto.  
  
 `psz`  
 Existente `CFixedStringT` que se copiará en este `CFixedStringT` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Debe tener en cuenta que la memoria se pueden producir excepciones cuando se utiliza el operador de asignación porque a menudo se asigna nuevo almacenamiento para contener resultante `CFixedStringT` objeto.  
  
## <a name="see-also"></a>Vea también  
 [CStringT (clase)](../../atl-mfc-shared/reference/cstringt-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases compartidas de ATL y MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)





