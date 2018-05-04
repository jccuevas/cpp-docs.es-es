---
title: Clase CPoint | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPoint
- ATLTYPES/ATL::CPoint
- ATLTYPES/ATL::CPoint::CPoint
- ATLTYPES/ATL::CPoint::Offset
dev_langs:
- C++
helpviewer_keywords:
- LPPOINT structure
- POINT structure
- CPoint class
ms.assetid: a6d4db93-35cc-444d-9221-c3e160f6edaa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36dc82c03f13b4708d705d9fd66eff26870c8346
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="cpoint-class"></a>Clase CPoint
Similar a la estructura `POINT` de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CPoint : public tagPOINT 
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPoint::CPoint](#cpoint)|Construye un objeto `CPoint`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPoint::Offset](#offset)|Agrega valores a la **x** y **y** los miembros de la `CPoint`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPoint::operator-](#operator_-)|Devuelve la diferencia de un `CPoint` y un tamaño o la negación de un punto o la diferencia de tamaño entre dos puntos, o el desplazamiento por un tamaño negativo.|  
|[CPoint::operator! =](#operator_neq)|Comprueba la desigualdad entre dos puntos.|  
|[CPoint::operator +](#operator_add)|Devuelve la suma de un `CPoint` y un tamaño o un punto, o un `CRect` desplazamiento por un tamaño.|  
|[CPoint::operator +=](#operator_add_eq)|Los desplazamientos `CPoint` mediante la adición de un tamaño o un punto.|  
|[CPoint::operator =](#operator_-_eq)|Los desplazamientos `CPoint` restando un tamaño o un punto.|  
|[CPoint::operator ==](#operator_eq_eq)|Comprueba la igualdad entre dos puntos.|  
  
## <a name="remarks"></a>Comentarios  
 También incluye funciones de miembro para manipular `CPoint` y [punto](../../mfc/reference/point-structure1.md) estructuras.  
  
 A `CPoint` objeto puede ser utilizado, donde un `POINT` usa una estructura. Los operadores de esta clase que interactúan con un "tamaño" aceptan [CSize](../../atl-mfc-shared/reference/csize-class.md) objetos o [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructuras, puesto que los dos son intercambiables.  
  
> [!NOTE]
>  Esta clase se deriva de la `tagPOINT` estructura. (El nombre `tagPOINT` es un nombre de uso menos frecuente para la `POINT` estructura.) Esto significa que los miembros de datos de la `POINT` estructura, `x` y `y`, son miembros de datos accesibles de `CPoint`.  
  
> [!NOTE]
>  Para obtener más información sobre comparten las clases de utilidad (como `CPoint`), consulte [clases compartidas](../../atl-mfc-shared/atl-mfc-shared-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `tagPOINT`  
  
 `CPoint`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atltypes.h  
  
##  <a name="cpoint"></a>  CPoint::CPoint
 Construye un objeto `CPoint`.  
  
```  
CPoint() throw();
CPoint(int initX, int initY) throw();
CPoint(POINT initPt) throw();
CPoint(SIZE initSize) throw();
CPoint(LPARAM dwPoint) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `initX`  
 Especifique el valor del miembro `x` de `CPoint`.  
  
 `initY`  
 Especifique el valor del miembro `y` de `CPoint`.  
  
 `initPt`  
 [PUNTO de](../../mfc/reference/point-structure1.md) estructura o `CPoint` que especifica los valores utilizados para inicializar `CPoint`.  
  
 `initSize`  
 [TAMAÑO](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura o [CSize](../../atl-mfc-shared/reference/csize-class.md) que especifica los valores utilizados para inicializar `CPoint`.  
  
 `dwPoint`  
 Establece el miembro `x` en la palabra de orden inferior de `dwPoint` y el miembro `y` en la palabra de orden superior de `dwPoint`.  
  
### <a name="remarks"></a>Comentarios  
 Si no se proporcionan argumentos, los miembros `x` e `y` se establecen en 0.  
  
### <a name="example"></a>Ejemplo  
  
```cpp   
CPoint   ptTopLeft(0, 0); 
// works from a POINT, too  
 
POINT   ptHere;  
ptHere.x = 35;  
ptHere.y = 95;  
 
CPoint   ptMFCHere(ptHere);
 
// works from a SIZE 
SIZE   sHowBig;  
sHowBig.cx = 300;  
sHowBig.cy = 10;  
 
CPoint ptMFCBig(sHowBig); 
// or from a DWORD  
 
DWORD   dwSize;  
dwSize = MAKELONG(35, 95);
 
CPoint ptFromDouble(dwSize);
ASSERT(ptFromDouble == ptMFCHere);
```  
  
##  <a name="offset"></a>  CPoint::Offset  
 Agrega valores a la **x** y **y** los miembros de la `CPoint`.  
  
```  
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *xOffset*  
 Especifica la cantidad necesaria para desplazar la **x** miembro de la `CPoint`.  
  
 *yOffset*  
 Especifica la cantidad necesaria para desplazar la **y** miembro de la `CPoint`.  
  
 `point`  
 Especifica la cantidad ( [punto](../../mfc/reference/point-structure1.md) o `CPoint`) para desplazar el `CPoint`.  
  
 `size`  
 Especifica la cantidad ( [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) o [CSize](../../atl-mfc-shared/reference/csize-class.md)) para desplazar el `CPoint`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]  
  
##  <a name="operator_eq_eq"></a>  CPoint::operator ==  
 Comprueba la igualdad entre dos puntos.  
  
```  
BOOL operator==(POINT point) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `point`  
 Contiene un [punto](../../mfc/reference/point-structure1.md) estructura o `CPoint` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si los puntos son iguales; en caso contrario es 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]  
  
##  <a name="operator_neq"></a>  CPoint::operator! =  
 Comprueba la desigualdad entre dos puntos.  
  
```  
BOOL operator!=(POINT point) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `point`  
 Contiene un [punto](../../mfc/reference/point-structure1.md) estructura o `CPoint` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si los puntos no son iguales; en caso contrario es 0.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]  
  
##  <a name="operator_add_eq"></a>  CPoint::operator +=  
 La primera sobrecarga agrega un tamaño para el `CPoint`.  
  
```  
void operator+=(SIZE size) throw(); 
void operator+=(POINT point) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `size`  
 Contiene un [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura o [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.  
  
 `point`  
 Contiene un [punto](../../mfc/reference/point-structure1.md) estructura o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 La segunda sobrecarga agrega un punto para la `CPoint`.  
  
 En ambos casos, la suma se realiza mediante la adición de la **x** (o **cx**) miembro del operando derecho a la **x** miembro de la `CPoint` y agregando el **y**  (o **cy**) miembro del operando derecho a la **y** miembro de la `CPoint`.  
  
 Por ejemplo, si agrega `CPoint(5, -7)` a una variable que contiene `CPoint(30, 40)` cambia la variable a `CPoint(35, 33)`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]  
  
##  <a name="operator_-_eq"></a>  CPoint::operator =  
 La primera sobrecarga resta un tamaño de la `CPoint`.  
  
```  
void operator-=(SIZE size) throw(); 
void operator-=(POINT point) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `size`  
 Contiene un [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura o [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.  
  
 `point`  
 Contiene un [punto](../../mfc/reference/point-structure1.md) estructura o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 La segunda sobrecarga resta un punto desde el `CPoint`.  
  
 En ambos casos, la resta se realiza restando el **x** (o **cx**) miembro del operando derecho de la **x** miembro de la `CPoint` y restando el **y** (o **cy**) miembro del operando derecho de la **y** miembro de la `CPoint`.  
  
 Por ejemplo, restar `CPoint(5, -7)` desde una variable que contiene `CPoint(30, 40)` cambia la variable a `CPoint(25, 47)`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]  
  
##  <a name="operator_add"></a>  CPoint::operator +  
 Usar este operador para compensar la `CPoint` por una `CPoint` o `CSize` objeto, o para desplazar una `CRect` por un `CPoint`.  
  
```  
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `size`  
 Contiene un [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura o [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.  
  
 `point`  
 Contiene un [punto](../../mfc/reference/point-structure1.md) estructura o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto.  
  
 `lpRect`  
 Contiene un puntero a un [RECT](../../mfc/reference/rect-structure1.md) estructura o [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 A `CPoint` que se desplaza por un tamaño de un **CPoint** que se desplaza por un punto o un **CRect** desplazamiento por un punto.  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo, mediante una de las primeras dos sobrecargas para desplazar el punto de `CPoint(25, -19)` por un punto de `CPoint(15, 5)` o tamaño `CSize(15, 5)` devuelve el valor `CPoint(40, -14)`.  
  
 Cuando se agrega un rectángulo a un punto de devuelve el rectángulo después de que se desplaza por la **x** y **y** valores especificados en el punto. Por ejemplo, mediante la última sobrecarga en el desplazamiento de un rectángulo `CRect(125, 219, 325, 419)` por un punto de `CPoint(25, -19)` devuelve `CRect(150, 200, 350, 400)`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]  
  
##  <a name="operator_-"></a>  CPoint::operator-  
 Utilice uno de las primeros dos sobrecargas para restar un `CPoint` o `CSize` objeto `CPoint`.  
  
```  
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `point`  
 A [punto](../../mfc/reference/point-structure1.md) estructura o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto.  
  
 `size`  
 A [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura o [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.  
  
 `lpRect`  
 Un puntero a un [RECT](../../mfc/reference/rect-structure1.md) estructura o un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 A `CSize` que es la diferencia entre dos puntos, un `CPoint` que se desplaza por la negación de un tamaño, un `CRect` que se desplaza por la negación de un punto o un `CPoint` que es la negación de un punto.  
  
### <a name="remarks"></a>Comentarios  
 La tercera sobrecarga desplazamientos un `CRect` por la negación de `CPoint`. Por último, utilice el operador unario para negar `CPoint`.  
  
 Por ejemplo, con la primera sobrecarga para buscar la diferencia entre dos puntos `CPoint(25, -19)` y `CPoint(15, 5)` devuelve `CSize(10, -24)`.  
  
 Restar un `CSize` de `CPoint` realiza el mismo cálculo anterior pero devuelve un `CPoint` el objeto, no es un `CSize` objeto. Por ejemplo, con la segunda sobrecarga para buscar la diferencia entre el punto de `CPoint(25, -19)` y el tamaño `CSize(15, 5)` devuelve `CPoint(10, -24)`.  
  
 Restar un rectángulo desde un punto, devuelve el desplazamiento de rectángulo por los negativos de la **x** y **y** valores especificados en el punto. Por ejemplo, mediante la última sobrecarga para compensar el rectángulo `CRect(125, 200, 325, 400)` por el punto de `CPoint(25, -19)` devuelve `CRect(100, 219, 300, 419)`.  
  
 Utilice el operador unario para negar un punto. Por ejemplo, mediante el operador unario con el punto de `CPoint(25, -19)` devuelve `CPoint(-25, 19)`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MDI de MFC](../../visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [POINT (estructura)](../../mfc/reference/point-structure1.md)   
 [CRect (clase)](../../atl-mfc-shared/reference/crect-class.md)   
 [CSize (clase)](../../atl-mfc-shared/reference/csize-class.md)



