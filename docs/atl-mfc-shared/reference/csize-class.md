---
title: Clase CSize | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSize
- ATLTYPES/ATL::CSize
- ATLTYPES/ATL::CSize::CSize
dev_langs: C++
helpviewer_keywords:
- SIZE
- dimensions, MFC
- dimensions
- CSize class
ms.assetid: fb2cf85a-0bc1-46f8-892b-309c108b52ae
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ac18decc8a2bb6bbc2d9e9677640eba67c85077e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="csize-class"></a>Clase CSize
Similar a la estructura [SIZE](http://msdn.microsoft.com/library/windows/desktop/dd145106) de Windows, que implementa una coordenada relativa o una posición.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CSize : public tagSIZE 
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSize::CSize](#csize)|Construye un objeto `CSize`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSize::operator-](#operator_-)|Resta dos tamaños.|  
|[CSize::operator! =](#operator_neq)|Comprueba la desigualdad entre `CSize` y un tamaño.|  
|[CSize::operator +](#operator_add)|Agrega dos tamaños.|  
|[CSize::operator +=](#operator_add_eq)|Agrega un tamaño para `CSize`.|  
|[CSize::operator =](#operator_-_eq)|Resta un tamaño de `CSize`.|  
|[CSize::operator ==](#operator_eq_eq)|Comprueba la igualdad entre `CSize` y un tamaño.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase se deriva de la **tamaño** estructura. Esto significa que puede pasar un `CSize` en un parámetro que requiere un **tamaño** y que los miembros de datos de la **tamaño** estructura son miembros de datos accesibles de `CSize`.  
  
 El **cx** y **cy** los miembros de **tamaño** (y `CSize`) son públicos. Además, `CSize` implementa las funciones miembro para manipular el **tamaño** estructura.  
  
> [!NOTE]
>  Para obtener más información sobre comparten las clases de utilidad (como `CSize`), consulte [clases compartidas](../../atl-mfc-shared/atl-mfc-shared-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `tagSIZE`  
  
 `CSize`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atltypes.h  
  
##  <a name="csize"></a>CSize::CSize  
 Construye un objeto `CSize`.  
  
```  
CSize() throw();
CSize( int initCX, int initCY) throw();
CSize( SIZE initSize) throw();
CSize( POINT initPt) throw();
CSize( DWORD dwSize) throw(); 
```  
  
### <a name="parameters"></a>Parámetros  
 *initCX*  
 Establece el **cx** miembro para el `CSize`.  
  
 *initCY*  
 Establece el **cy** miembro para el `CSize`.  
  
 `initSize`  
 [TAMAÑO](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura o `CSize` objeto utilizado para inicializar `CSize`.  
  
 `initPt`  
 [PUNTO de](../../mfc/reference/point-structure1.md) estructura o `CPoint` objeto utilizado para inicializar `CSize`.  
  
 `dwSize`  
 `DWORD`utilizado para inicializar `CSize`. La palabra de orden inferior es la **cx** miembro y la palabra de orden superior es el **cy** miembro.  
  
### <a name="remarks"></a>Comentarios  
 Si no se proporcionan argumentos, **cx** y **cy** se inicializan en cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]  
  
##  <a name="operator_eq_eq"></a>CSize::operator ==  
 Comprueba la igualdad entre dos tamaños.  
  
```   
BOOL operator==(SIZE size) const throw(); 
```  
  
### <a name="remarks"></a>Comentarios  
 Devuelve distinto de cero si los tamaños son iguales, otherwize 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]  
  
##  <a name="operator_neq"></a>CSize::operator! =  
 Comprueba la desigualdad entre dos tamaños.  
  
```   
BOOL operator!=(SIZE size) const throw(); 
```  
  
### <a name="remarks"></a>Comentarios  
 Devuelve un valor distinto de cero si no son iguales, los tamaños de lo contrario, 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]  
  
##  <a name="operator_add_eq"></a>CSize::operator +=  
 Agrega un tamaño a este `CSize`.  
  
```   
void operator+=(SIZE size) throw(); 
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]  
  
##  <a name="operator_-_eq"></a>CSize::operator =  
 Resta un tamaño de este `CSize`.  
  
```   
void operator-=(SIZE size) throw(); 
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]  
  
##  <a name="operator_add"></a>CSize::operator +  
 Estos operadores agregar este `CSize` valor para el valor del parámetro.  
  
```   
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw(); 
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte las siguientes descripciones de los operadores individuales:  
  
- **operador + (** `size` **)**esta operación agrega dos `CSize` valores.  
  
- **operador + (** `point` **)**esta operación desplaza (mueve) un [punto](http://msdn.microsoft.com/library/windows/desktop/dd162805) (o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) valor por este `CSize` valor. El **cx** y **cy** los miembros de este `CSize` valor se agregan a la **x** y **y** miembros de datos de la **punto**  valor. Este bloque es análogo a la versión de [CPoint::operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) que toma un [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) parámetro.  
  
- **operador + (** `lpRect` **)**esta operación desplaza (mueve) un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) (o [CRect](../../atl-mfc-shared/reference/crect-class.md)) valor por este `CSize` valor. El **cx** y **cy** los miembros de este `CSize` valor se agregan a la **izquierdo**, **arriba**, **derecha**, y **inferior** miembros de datos de la `RECT` valor. Este bloque es análogo a la versión de [CRect::operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add) que toma un [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) parámetro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]  
  
##  <a name="operator_-"></a>CSize::operator-  
 Las tres primeras de estos operadores restar esto `CSize` valor para el valor del parámetro.  
  
```   
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw(); 
```  
  
### <a name="remarks"></a>Comentarios  
 El cuarto operador, el operador unario menos, cambia el signo de la `CSize` valor. Consulte las siguientes descripciones de los operadores individuales:  
  
- **operador-(** `size` **)**esta operación de resta dos `CSize` valores.  
  
- **operador-(** `point` **)**esta operación desplaza (mueve) un [punto](http://msdn.microsoft.com/library/windows/desktop/dd162805) o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) valor por el inverso aditivo de este `CSize` valor. El **cx** y **cy** de este `CSize` se resta el valor de la **x** y **y** miembros de datos de la **punto**  valor. Este bloque es análogo a la versión de [CPoint::operator -](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) que toma un [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) parámetro.  
  
- **operador-(** `lpRect` **)**esta operación desplaza (mueve) un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) o [CRect](../../atl-mfc-shared/reference/crect-class.md) valor por el inverso aditivo de este `CSize` valor. El **cx** y **cy** los miembros de este `CSize` se resta el valor de la **izquierdo**, **arriba**, **derecha**, y **inferior** miembros de datos de la `RECT` valor. Este bloque es análogo a la versión de [CRect::operator -](../../atl-mfc-shared/reference/crect-class.md#operator_-) que toma un [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) parámetro.  
  
- **operador-()**esta operación devuelve el inverso aditivo de este `CSize` valor.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MDI de MFC](../../visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CRect (clase)](../../atl-mfc-shared/reference/crect-class.md)   
 [CPoint (clase)](../../atl-mfc-shared/reference/cpoint-class.md)

