---
title: "CRect (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRect"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LPCRECT (tipo de datos)"
  - "CRect (clase)"
  - "Operador LPRECT"
  - "RECT (estructura)"
ms.assetid: dee4e752-15d6-4db4-b68f-1ad65b2ed6ca
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRect (clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Similar a Windows [RECT](../../mfc/reference/rect-structure1.md) estructura.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CRect : public tagRECT  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRect::CRect](#crect__crect)|Construye un objeto `CRect`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRect::BottomRight](#crect__bottomright)|Devuelve el punto de la esquina inferior derecha de `CRect`.|  
|[CRect::CenterPoint](#crect__centerpoint)|Devuelve el punto central de `CRect`.|  
|[CRect::CopyRect](#crect__copyrect)|Copia las dimensiones de un rectángulo de origen a `CRect`.|  
|[CRect::DeflateRect](#crect__deflaterect)|Reduce el ancho y alto de `CRect`.|  
|[CRect::EqualRect](#crect__equalrect)|Determina si `CRect` es igual que el rectángulo especificado.|  
|[CRect::Height](#crect__height)|Calcula el alto de `CRect`.|  
|[CRect::InflateRect](#crect__inflaterect)|Aumenta el ancho y alto de `CRect`.|  
|[CRect::IntersectRect](#crect__intersectrect)|Conjuntos de `CRect` igual a la intersección de dos rectángulos.|  
|[CRect::IsRectEmpty](#crect__isrectempty)|Determina si `CRect` está vacía. `CRect` está vacío si el ancho o alto es 0.|  
|[CRect::IsRectNull](#crect__isrectnull)|Determina si el **arriba**, **inferior**, **izquierdo**, y **derecha** variables de miembro son iguales a 0.|  
|[CRect::MoveToX](#crect__movetox)|Mueve `CRect` a la coordenada x especificada.|  
|[CRect::MoveToXY](#crect__movetoxy)|Mueve `CRect` a las coordenadas x e y especificadas.|  
|[CRect::MoveToY](#crect__movetoy)|Mueve `CRect` a la coordenada y especificada.|  
|[CRect:: NormalizeRect](#crect__normalizerect)|Estandariza el alto y ancho de `CRect`.|  
|[CRect::OffsetRect](#crect__offsetrect)|Mueve `CRect` por los desplazamientos indicados.|  
|[CRect::PtInRect](#crect__ptinrect)|Determina si el punto especificado está dentro de `CRect`.|  
|[CRect::SetRect](#crect__setrect)|Establece las dimensiones de `CRect`.|  
|[CRect::SetRectEmpty](#crect__setrectempty)|Conjuntos de `CRect` a un rectángulo vacío (todas las coordenadas igual a 0).|  
|[CRect::Size](#crect__size)|Calcula el tamaño de `CRect`.|  
|[CRect::SubtractRect](#crect__subtractrect)|Resta un rectángulo de otro.|  
|[CRect::TopLeft](#crect__topleft)|Devuelve el punto superior izquierdo del `CRect`.|  
|[CRect::UnionRect](#crect__unionrect)|Conjuntos de `CRect` igual que la unión de dos rectángulos.|  
|[CRect::Width](#crect__width)|Calcula el ancho de `CRect`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRect::operator-](#crect__operator_-)|Resta los desplazamientos especificados de `CRect` o desinfla `CRect` y devuelve resultante `CRect`.|  
|[CRect::operator LPCRECT](#crect__operator_lpcrect)|Convierte un `CRect` para un **LPCRECT**.|  
|[CRect::operator LPRECT](#crect__operator_lprect)|Convierte un `CRect` para un `LPRECT`.|  
|[CRect::operator! =](#crect__operator__neq)|Determina si `CRect` no es igual a un rectángulo.|  
|[CRect::operator &amp;](#crect__operator__amp_)|Crea la intersección de `CRect` y un rectángulo y devuelve resultante `CRect`.|  
|[CRect::operator &amp;=](#crect__operator__amp__eq)|Conjuntos de `CRect` igual a la intersección de `CRect` y un rectángulo.|  
|[CRect::operator |](#crect__operator__or)|Crea la unión de `CRect` y un rectángulo y devuelve resultante `CRect`.|  
|[CRect::operator |=](#crect__operator__or_eq)|Conjuntos de `CRect` igual que la unión de `CRect` y un rectángulo.|  
|[CRect::operator +](#crect__operator__add)|Agrega los desplazamientos especificados a `CRect` o infla `CRect` y devuelve resultante `CRect`.|  
|[CRect::operator +=](#crect__operator__add_eq)|Agrega los desplazamientos especificados a `CRect` o infla `CRect`.|  
|[CRect::operator =](#crect__operator__eq)|Copia las dimensiones de un rectángulo a `CRect`.|  
|[CRect::operator =](#crect__operator_-_eq)|Resta los desplazamientos especificados de `CRect` o desinfla `CRect`.|  
|[CRect::operator ==](#crect__operator__eq_eq)|Determina si `CRect` es igual a un rectángulo.|  
  
## <a name="remarks"></a>Comentarios  
 `CRect` También incluye funciones de miembro para manipular `CRect` objetos y Windows `RECT` estructuras.  
  
 Un `CRect` objeto se puede pasar como un parámetro de función siempre que sea un `RECT` estructura, **LPCRECT**, o `LPRECT` puede pasarse.  
  
> [!NOTE]
>  Esta clase se deriva de la **tagRECT** estructura. (El nombre **tagRECT** es un nombre de menos utilizadas para el `RECT` estructura.) Esto significa que los miembros de datos ( **izquierdo**, **arriba**, **derecho**, y **inferior**) de la `RECT` estructura son miembros de datos accesibles a través de `CRect`.  
  
 Un `CRect` contiene variables de miembro que definen los puntos de la parte superior izquierda e inferior derecha de un rectángulo.  
  
 Al especificar un `CRect`, debe tener cuidado para crearlo para que se ha normalizado, es decir, que el valor de la coordenada izquierda sea inferior a la derecha y la parte superior es menor que la parte inferior. Por ejemplo, una parte superior izquierda de (10,10) y parte inferior derecha (20,20) define un rectángulo normalizado pero superior izquierda de (20,20) y parte inferior derecha (10,10) define un rectángulo no normalizado. Si el rectángulo no está normalizado, muchas `CRect` funciones miembro pueden devolver resultados incorrectos. (Consulte [CRect:: NormalizeRect](#crect__normalizerect) para obtener una lista de estas funciones.) Antes de llamar a una función que requiera rectángulos normalizados, puede normalizar rectángulos no normalizado mediante una llamada a la `NormalizeRect` (función).  
  
 Tenga cuidado al manipular un `CRect` con el [CDC::DPtoLP] (.. /Topic/CDC%20Class.MD#cdc__dptolp y [CDC::LPtoDP] (.. Funciones de miembro /topic/CDC%20Class.MD#cdc__lptodp. Si el modo de asignación de un contexto de presentación es tal que la extensión y es negativa, como en `MM_LOENGLISH`, a continuación, `CDC::DPtoLP` transformará el `CRect` para que sus principales es mayor que la parte inferior. Funciones como **alto** y **tamaño** devolverá valores negativos para el alto de transformado `CRect`, y el rectángulo será no normalizado.  
  
 Si utiliza sobrecargado `CRect` operadores, el primer operando debe ser un `CRect`; el segundo puede ser un [RECT](../../mfc/reference/rect-structure1.md) estructura o un `CRect` objeto.  
  
> [!NOTE]
>  Para obtener más información sobre comparten las clases de utilidad (como `CRect`), consulte [clases compartidas](../../atl-mfc-shared/atl-mfc-shared-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `tagRECT`  
  
 `CRect`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atltypes.h  
  
##  <a name="a-namecrectbottomrighta-crectbottomright"></a><a name="crect__bottomright"></a>  CRect::BottomRight  
 Las coordenadas se devuelven como una referencia a un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto que se encuentra en `CRect`.  
  
```  
 
CPoint& BottomRight() throw();

const CPoint& BottomRight() const throw();

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Las coordenadas de la esquina inferior derecha del rectángulo.  
  
### <a name="remarks"></a>Comentarios  
 Puede utilizar esta función para obtener o establecer la esquina inferior derecha del rectángulo. Establecer la esquina mediante esta función en el lado izquierdo del operador de asignación.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#35](../../atl-mfc-shared/codesnippet/CPP/crect-class_1.cpp)]  
  
##  <a name="a-namecrectcenterpointa-crectcenterpoint"></a><a name="crect__centerpoint"></a>  CRect::CenterPoint  
 Calcula el punto central de `CRect` sumar los valores de la izquierda y derecho y dividiendo por dos y se agregan los valores superior e inferior y dividir por dos.  
  
```  
CPoint CenterPoint() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CPoint` objeto que es el punto central de `CRect`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#36](../../atl-mfc-shared/codesnippet/CPP/crect-class_2.cpp)]  
  
##  <a name="a-namecrectcopyrecta-crectcopyrect"></a><a name="crect__copyrect"></a>  CRect::CopyRect  
 Copia el `lpSrcRect` rectángulo en `CRect`.  
  
```  
 
void CopyRect(
LPCRECT   
lpSrcRect) throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 `lpSrcRect`  
 Apunta a la [RECT](../../mfc/reference/rect-structure1.md) estructura o `CRect` objeto que se va a copiar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#37](../../atl-mfc-shared/codesnippet/CPP/crect-class_3.cpp)]  
  
##  <a name="a-namecrectcrecta-crectcrect"></a><a name="crect__crect"></a>  CRect::CRect  
 Construye un objeto `CRect`.  
  
```  
 
    CRect() throw();
CRect(
 int    
    l ,  
    int 
    t ,  
    int 
    r ,  
    int 
    b) throw();
CRect(
 const RECT& 
    srcRect) throw();
CRect(
 LPCRECT    
    lpSrcRect) throw();
CRect(
 POINT    
    point ,  
    SIZE 
    size) throw();
CRect(
 POINT    
    topLeft ,  
    POINT 
    bottomRight) throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 *l*  
 Especifica la posición izquierda de `CRect`.  
  
 *t*  
 Especifica la parte superior de `CRect`.  
  
 *r*  
 Especifica la posición correcta de `CRect`.  
  
 *b*  
 Especifica la parte inferior de `CRect`.  
  
 *srcRect*  
 Hace referencia a la [RECT](../../mfc/reference/rect-structure1.md) estructura con las coordenadas para `CRect`.  
  
 `lpSrcRect`  
 Apunta a la `RECT` estructura con las coordenadas para `CRect`.  
  
 `point`  
 Especifica el punto de origen para el rectángulo que se va a construir. Corresponde a la esquina superior izquierda.  
  
 `size`  
 Especifica el desplazamiento desde la esquina superior izquierda a la esquina inferior derecha del rectángulo que se va a construir.  
  
 *topLeft*  
 Especifica la posición de la esquina superior izquierda de `CRect`.  
  
 *bottomRight*  
 Especifica la posición de la esquina inferior derecha de `CRect`.  
  
### <a name="remarks"></a>Comentarios  
 Si no se proporcionan argumentos, **izquierdo**, **arriba**, **derecho**, y **inferior** miembros no se inicializan.  
  
 El `CRect`( **RECT const &**) y `CRect`( **LPCRECT**) constructores realizan una [CopyRect](#crect__copyrect). Los otros constructores inicializan las variables miembro del objeto directamente.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#38](../../atl-mfc-shared/codesnippet/CPP/crect-class_4.cpp)]  
  
##  <a name="a-namecrectdeflaterecta-crectdeflaterect"></a><a name="crect__deflaterect"></a>  CRect::DeflateRect  
 `DeflateRect` desinfla `CRect` moviendo sus lados hacia su centro.  
  
```  
 
    void DeflateRect(
    int 
    x ,  
    int 
    y) throw();
void DeflateRect(
    SIZE 
    size) throw();
void DeflateRect(
    LPCRECT 
    lpRect) throw();
void DeflateRect(
    int 
    l ,  
    int 
    t ,  
    int 
    r ,  
    int 
    b) throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica el número de unidades para disminuir la izquierda y derecha de `CRect`.  
  
 *y*  
 Especifica el número de unidades para disminuir la parte superior e inferior de `CRect`.  
  
 `size`  
 Un [TAMAÑO](http://msdn.microsoft.com/library/windows/desktop/dd145106) o [CSize](../../atl-mfc-shared/reference/csize-class.md) que especifica el número de unidades para deflate `CRect`. El `cx` valor especifica el número de unidades para disminuir los lados izquierdo y derecho y el `cy` valor especifica el número de unidades para disminuir la parte superior e inferior.  
  
 `lpRect`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura o `CRect` que especifica el número de unidades para deflate cada lado.  
  
 *l*  
 Especifica el número de unidades de deflate del lado izquierdo del `CRect`.  
  
 *t*  
 Especifica el número de unidades para disminuir la parte superior de `CRect`.  
  
 *r*  
 Especifica el número de unidades para disminuir el lado derecho de `CRect`.  
  
 *b*  
 Especifica el número de unidades para disminuir la parte inferior de `CRect`.  
  
### <a name="remarks"></a>Comentarios  
 Para ello, `DeflateRect` agrega unidades a la izquierda y la parte superior y se resta de unidades de la derecha e inferior. Los parámetros de `DeflateRect` están firmados valores; los valores positivos deflate `CRect` y los valores negativos infla.  
  
 Las primeras dos sobrecargas deflate ambos pares de lados opuestos de `CRect` para que su ancho total se reduce a dos veces *x* (o `cx`) y su altura total se reduce por dos veces *y* (o `cy`). Las dos sobrecargas deflate cada lado del `CRect` independientemente de las otras.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#39](../../atl-mfc-shared/codesnippet/CPP/crect-class_5.cpp)]  
  
##  <a name="a-namecrectequalrecta-crectequalrect"></a><a name="crect__equalrect"></a>  CRect::EqualRect  
 Determina si `CRect` es igual que el rectángulo especificado.  
  
```  
 
BOOL EqualRect(
LPCRECT   
lpRect) const throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura o `CRect` objeto que contiene las coordenadas de la esquina superior izquierda e inferior derecha de un rectángulo.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si los dos rectángulos tienen el mismo superior, izquierda, inferior y derecho valores; en caso contrario, 0.  
  
> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#crect__normalizerect) normalizar los rectángulos antes de llamar a esta función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#40](../../atl-mfc-shared/codesnippet/CPP/crect-class_6.cpp)]  
  
##  <a name="a-namecrectheighta-crectheight"></a><a name="crect__height"></a>  CRect::Height  
 Calcula el alto de `CRect` restando el valor superior del valor de la parte inferior.  
  
```  
int Height() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El alto de `CRect`.  
  
### <a name="remarks"></a>Comentarios  
 El valor resultante puede ser negativo.  
  
> [!NOTE]
>  Se debe normalizar el rectángulo o esta función puede producir un error. Puede llamar a [NormalizeRect](#crect__normalizerect) normalizar el rectángulo antes de llamar a esta función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#41](../../atl-mfc-shared/codesnippet/CPP/crect-class_7.cpp)]  
  
##  <a name="a-namecrectinflaterecta-crectinflaterect"></a><a name="crect__inflaterect"></a>  CRect::InflateRect  
 `InflateRect` se infla `CRect` moviendo sus lados lejos de su centro.  
  
```  
 
    void InflateRect(
    int 
    x ,  
    int 
    y) throw();
void InflateRect(
    SIZE 
    size) throw();
void InflateRect(
    LPCRECT 
    lpRect) throw();
void InflateRect(
    int 
    l ,  
    int 
    t ,  
    int 
    r ,  
    int 
    b) throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica el número de unidades para aumentar la izquierda y derecha de `CRect`.  
  
 *y*  
 Especifica el número de unidades para aumentar la parte superior e inferior de `CRect`.  
  
 `size`  
 Un [TAMAÑO](http://msdn.microsoft.com/library/windows/desktop/dd145106) o [CSize](../../atl-mfc-shared/reference/csize-class.md) que especifica el número de unidades para aumentar `CRect`. El `cx` valor especifica el número de unidades para aumentar los lados izquierdo y derecho y el `cy` valor especifica el número de unidades para aumentar la parte superior e inferior.  
  
 `lpRect`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura o `CRect` que especifica el número de unidades para aumentar cada lado.  
  
 *l*  
 Especifica el número de unidades para aumentar el lado izquierdo del `CRect`.  
  
 *t*  
 Especifica el número de unidades para aumentar la parte superior de `CRect`.  
  
 *r*  
 Especifica el número de unidades para aumentar el lado derecho de `CRect`.  
  
 *b*  
 Especifica el número de unidades para aumentar la parte inferior de `CRect`.  
  
### <a name="remarks"></a>Comentarios  
 Para ello, `InflateRect` resta unidades de la izquierda y la parte superior y agrega unidades a la derecha e inferior. Los parámetros de `InflateRect` están firmados valores; positivo valores infla `CRect` y los valores negativos deflate.  
  
 Las primeras dos sobrecargas aumentar ambos pares de lados opuestos de `CRect` para que su ancho total se incrementa en dos veces *x* (o `cx`) y su altura total se incrementa en dos veces *y* (o `cy`). Las dos sobrecargas aumentar cada lado del `CRect` independientemente de las otras.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#42](../../atl-mfc-shared/codesnippet/CPP/crect-class_8.cpp)]  
  
##  <a name="a-namecrectintersectrecta-crectintersectrect"></a><a name="crect__intersectrect"></a>  CRect::IntersectRect  
 Realiza una `CRect` igual a la intersección de dos rectángulos existentes.  
  
```  
 
    BOOL IntersectRect(
    LPCRECT 
    lpRect1 ,  
    LPCRECT 
    lpRect2) throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect1`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura o `CRect` objeto que contiene un rectángulo de origen.  
  
 `lpRect2`  
 Apunta a un `RECT` estructura o `CRect` objeto que contiene un rectángulo de origen.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la intersección no está vacía; 0 si la intersección está vacía.  
  
### <a name="remarks"></a>Comentarios  
 La intersección es el rectángulo más grande que contiene ambos rectángulos existentes.  
  
> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#crect__normalizerect) normalizar los rectángulos antes de llamar a esta función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#43](../../atl-mfc-shared/codesnippet/CPP/crect-class_9.cpp)]  
  
##  <a name="a-namecrectisrectemptya-crectisrectempty"></a><a name="crect__isrectempty"></a>  CRect::IsRectEmpty  
 Determina si `CRect` está vacía.  
  
```  
BOOL IsRectEmpty() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si `CRect` está vacía; 0 si `CRect` no está vacío.  
  
### <a name="remarks"></a>Comentarios  
 Un rectángulo está vacío si el ancho o alto es 0 o negativo. Difiere de `IsRectNull`, que determina si todas las coordenadas del rectángulo son cero.  
  
> [!NOTE]
>  Se debe normalizar el rectángulo o esta función puede producir un error. Puede llamar a [NormalizeRect](#crect__normalizerect) normalizar el rectángulo antes de llamar a esta función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#44](../../atl-mfc-shared/codesnippet/CPP/crect-class_10.cpp)]  
  
##  <a name="a-namecrectisrectnulla-crectisrectnull"></a><a name="crect__isrectnull"></a>  CRect::IsRectNull  
 Determina si la parte superior, izquierda, abajo y a la derecha los valores de `CRect` son iguales a 0.  
  
```  
BOOL IsRectNull() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si `CRect`de la parte superior, izquierda, inferior y derecho valores son todos igual a 0; de lo contrario 0.  
  
### <a name="remarks"></a>Comentarios  
 Difiere de `IsRectEmpty`, que determina si el rectángulo está vacío.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#45](../../atl-mfc-shared/codesnippet/CPP/crect-class_11.cpp)]  
  
##  <a name="a-namecrectmovetoxa-crectmovetox"></a><a name="crect__movetox"></a>  CRect::MoveToX  
 Llame a esta función para mover el rectángulo que especifica la coordenada x absoluta *x*.  
  
```  
 
void MoveToX(
int   
x) throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Coordenada x absoluta de la esquina superior izquierda del rectángulo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#46](../../atl-mfc-shared/codesnippet/CPP/crect-class_12.cpp)]  
  
##  <a name="a-namecrectmovetoxya-crectmovetoxy"></a><a name="crect__movetoxy"></a>  CRect::MoveToXY  
 Llame a esta función para mover el rectángulo a la absoluta - coordenadas x e y-especificada.  
  
```  
 
    void MoveToXY(
    int 
    x ,  
    int 
    y) throw();
void MoveToXY(
    POINT 
    point) throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Coordenada x absoluta de la esquina superior izquierda del rectángulo.  
  
 *y*  
 Coordenada y absoluta de la esquina superior izquierda del rectángulo.  
  
 `point`  
 Un **PUNTO** estructura que especifica la esquina superior izquierda absoluta del rectángulo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#47](../../atl-mfc-shared/codesnippet/CPP/crect-class_13.cpp)]  
  
##  <a name="a-namecrectmovetoya-crectmovetoy"></a><a name="crect__movetoy"></a>  CRect::MoveToY  
 Llame a esta función para mover el rectángulo a la coordenada absoluta especificada por *y*.  
  
```  
 
void MoveToY(
int   
y) throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 *y*  
 Coordenada y absoluta de la esquina superior izquierda del rectángulo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#48](../../atl-mfc-shared/codesnippet/CPP/crect-class_14.cpp)]  
  
##  <a name="a-namecrectnormalizerecta-crectnormalizerect"></a><a name="crect__normalizerect"></a>  CRect:: NormalizeRect  
 Normaliza `CRect` para que el alto y el ancho son positivos.  
  
```  
void NormalizeRect() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Se normaliza el rectángulo para colocar el cuadrante cuarto, que normalmente utiliza Windows de las coordenadas. `NormalizeRect` Compara los valores superior e inferior y puede intercambiarlos si la parte superior es mayor que la parte inferior. De forma similar, intercambia los valores de la izquierda y derecho si es mayor que el derecho de la izquierda. Esta función es útil cuando se trabaja con los modos de asignación diferente e invertido rectángulos.  
  
> [!NOTE]
>  La siguiente `CRect` funciones miembro requieren rectángulos normalizados para que funcione correctamente: [alto](#crect__height), [ancho](#crect__width), [tamaño](#crect__size), [IsRectEmpty](#crect__isrectempty), [PtInRect](#crect__ptinrect), [EqualRect](#crect__equalrect), [UnionRect](#crect__unionrect), [IntersectRect](#crect__intersectrect), [SubtractRect](#crect__subtractrect), [operador ==](#crect__operator__eq_eq), [operador! =](#crect__operator__neq), [operador &#124;](#crect__operator__or), [operador &#124; =](#crect__operator__or_eq), [operador &](#crect__operator__amp_), y [operador & =](#crect__operator__amp__eq).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#49](../../atl-mfc-shared/codesnippet/CPP/crect-class_15.cpp)]  
  
##  <a name="a-namecrectoffsetrecta-crectoffsetrect"></a><a name="crect__offsetrect"></a>  CRect::OffsetRect  
 Mueve `CRect` por los desplazamientos indicados.  
  
```  
 
    void OffsetRect(
    int 
    x ,  
    int 
    y) throw();
void OffsetRect(
    POINT 
    point) throw();
void OffsetRect(
    SIZE 
    size) throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Especifica la cantidad para mover a la izquierda o derecha. Debe ser negativo para moverse hacia la izquierda.  
  
 *y*  
 Especifica la cantidad para subir o Bajar. Debe ser negativo para mover hacia arriba.  
  
 `point`  
 Contiene un [PUNTO](../../mfc/reference/point-structure1.md) estructura o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) especificar ambas dimensiones por las que se va a mover el objeto.  
  
 `size`  
 Contiene un [TAMAÑO](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura o [CSize](../../atl-mfc-shared/reference/csize-class.md) especificar ambas dimensiones por las que se va a mover el objeto.  
  
### <a name="remarks"></a>Comentarios  
 Mueve `CRect`*x* unidades a lo largo del eje x y *y* unidades a lo largo del eje y. El *x* y *y* parámetros son valores con signo, así que `CRect` se puede mover izquierda o derecha y arriba o abajo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#50](../../atl-mfc-shared/codesnippet/CPP/crect-class_16.cpp)]  
  
##  <a name="a-namecrectoperatorlpcrecta-crectoperator-lpcrect"></a><a name="crect__operator_lpcrect"></a>  CRect::operator LPCRECT  
 Convierte un `CRect` para un [LPCRECT](../../mfc/reference/data-types-mfc.md).  
  
''' throw() const de operador LPCRECT();
```  
  
### Remarks  
 When you use this function, you don't need the address-of ( **&**) operator. This operator will be automatically used when you pass a `CRect` object to a function that expects an **LPCRECT**.  
  
### Example  
 [!code-cpp[NVC_ATLMFC_Utilities#58](../../atl-mfc-shared/codesnippet/CPP/crect-class_17.cpp)]  
  
##  <a name="crect__operator_lprect"></a>  CRect::operator LPRECT  
 Converts a `CRect` to an [LPRECT](../../mfc/reference/data-types-mfc.md).  
  
```  operator LPRECT() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Al usar esta función, no es necesario de dirección ( **&**) (operador). Este operador se utilizará automáticamente cuando se pasa un `CRect` objeto a una función que espera un `LPRECT`.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CRect::operator LPCRECT](#crect__operator_lpcrect).  
  
##  <a name="a-namecrectoperatoreqa-crectoperator-"></a><a name="crect__operator__eq"></a>  CRect::operator =  
 Asigna *srcRect* a `CRect`.  
  
```  
 
void operator=(
const RECT& 
srcRect) throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 *srcRect*  
 Hace referencia a un rectángulo de origen. Puede ser un [RECT](../../mfc/reference/rect-structure1.md) o `CRect`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#59](../../atl-mfc-shared/codesnippet/CPP/crect-class_18.cpp)]  
  
##  <a name="a-namecrectoperatoreqeqa-crectoperator-"></a><a name="crect__operator__eq_eq"></a>  CRect::operator ==  
 Determina si `rect` es igual a `CRect` comparando las coordenadas de la esquina superior izquierda e inferior derecha.  
  
```  
 
BOOL operator==(
const RECT& 
rect) const throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 `rect`  
 Hace referencia a un rectángulo de origen. Puede ser un [RECT](../../mfc/reference/rect-structure1.md) o `CRect`.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si son iguales; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#crect__normalizerect) normalizar los rectángulos antes de llamar a esta función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#60](../../atl-mfc-shared/codesnippet/CPP/crect-class_19.cpp)]  
  
##  <a name="a-namecrectoperatorneqa-crectoperator-"></a><a name="crect__operator__neq"></a>  CRect::operator! =  
 Determina si `rect` no es igual a `CRect` comparando las coordenadas de la esquina superior izquierda e inferior derecha.  
  
```  
 
BOOL operator!=(
const RECT& 
rect) const throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 `rect`  
 Hace referencia a un rectángulo de origen. Puede ser un [RECT](../../mfc/reference/rect-structure1.md) o `CRect`.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si no son iguales; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#crect__normalizerect) normalizar los rectángulos antes de llamar a esta función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#61](../../atl-mfc-shared/codesnippet/CPP/crect-class_20.cpp)]  
  
##  <a name="a-namecrectoperatoraddeqa-crectoperator-"></a><a name="crect__operator__add_eq"></a>  CRect::operator +=  
 Mover las primeras dos sobrecargas `CRect` por los desplazamientos indicados.  
  
```  
 
void operator+=(
POINT   
point) throw();

void operator+=(
SIZE   
size) throw();

void operator+=(
LPCRECT   
lpRect) throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 `point`  
 Un [PUNTO](../../mfc/reference/point-structure1.md) estructura o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto que especifica el número de unidades para mover el rectángulo.  
  
 `size`  
 Un [TAMAÑO](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura o [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que especifica el número de unidades para mover el rectángulo.  
  
 `lpRect`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura o `CRect` objeto que contiene el número de unidades para aumentar cada lado de `CRect`.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro *x* y *y* (o `cx` y `cy`) se agregan valores a `CRect`.  
  
 La tercera sobrecarga aumenta `CRect` por el número especificado de unidades de cada miembro del parámetro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#62](../../atl-mfc-shared/codesnippet/CPP/crect-class_21.cpp)]  
  
##  <a name="a-namecrectoperator-eqa-crectoperator--"></a><a name="crect__operator_-_eq"></a>  CRect::operator =  
 Mover las primeras dos sobrecargas `CRect` por los desplazamientos indicados.  
  
```  
 
void operator-=(
POINT   
point) throw();

void operator-=(
SIZE   
size) throw();

void operator-=(
LPCRECT   
lpRect) throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 `point`  
 Un [PUNTO](../../mfc/reference/point-structure1.md) estructura o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto que especifica el número de unidades para mover el rectángulo.  
  
 `size`  
 Un [TAMAÑO](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura o [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que especifica el número de unidades para mover el rectángulo.  
  
 `lpRect`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura o `CRect` objeto que contiene el número de unidades para deflate cada lado de `CRect`.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro *x* y *y* (o `cx` y `cy`) se restan valores `CRect`.  
  
 La tercera sobrecarga desinfla `CRect` por el número especificado de unidades de cada miembro del parámetro. Tenga en cuenta que esta sobrecarga funciona como [DeflateRect](#crect__deflaterect).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#63](../../atl-mfc-shared/codesnippet/CPP/crect-class_22.cpp)]  
  
##  <a name="a-namecrectoperatorampeqa-crectoperator-amp"></a><a name="crect__operator__amp__eq"></a>  CRect::operator &amp;=  
 Conjuntos de `CRect` igual a la intersección de `CRect` y `rect`.  
  
```  
 
void operator&=(
const RECT& 
rect) throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 `rect`  
 Contiene un [RECT](../../mfc/reference/rect-structure1.md) o `CRect`.  
  
### <a name="remarks"></a>Comentarios  
 La intersección es el rectángulo más grande que se encuentra en dos rectángulos.  
  
> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#crect__normalizerect) normalizar los rectángulos antes de llamar a esta función.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CRect::IntersectRect](#crect__intersectrect).  
  
##  <a name="a-namecrectoperatororeqa-crectoperator-124"></a><a name="crect__operator__or_eq"></a>  CRect::operator &#124; =  
 Conjuntos de `CRect` igual que la unión de `CRect` y `rect`.  
  
```  
 
void operator|=(
const RECT& 
rect) throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 `rect`  
 Contiene un `CRect` o [RECT](../../mfc/reference/rect-structure1.md).  
  
### <a name="remarks"></a>Comentarios  
 La unión es el rectángulo más pequeño que contiene dos rectángulos de origen.  
  
> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#crect__normalizerect) normalizar los rectángulos antes de llamar a esta función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#64](../../atl-mfc-shared/codesnippet/CPP/crect-class_23.cpp)]  
  
##  <a name="a-namecrectoperatoradda-crectoperator-"></a><a name="crect__operator__add"></a>  CRect::operator +  
 Las primeras dos sobrecargas devuelven un `CRect` objeto que es igual a `CRect` desplazado por los desplazamientos indicados.  
  
```  
 
CRect operator+(
POINT   
point) const throw();

CRect operator+(
LPCRECT   
lpRect) const throw();

CRect operator+(
SIZE   
size) const throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 `point`  
 Un [PUNTO](../../mfc/reference/point-structure1.md) estructura o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto que especifica el número de unidades para mover el valor devuelto.  
  
 `size`  
 Un [TAMAÑO](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura o [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que especifica el número de unidades para mover el valor devuelto.  
  
 `lpRect`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura o `CRect` objeto que contiene el número de unidades para aumentar cada lado del valor devuelto.  
  
### <a name="return-value"></a>Valor devuelto  
 El `CRect` resultante de mover o Inflar `CRect` por el número de unidades especificadas en el parámetro.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro *x* y *y* (o `cx` y `cy`) se agregan parámetros a `CRect`de posición.  
  
 La tercera sobrecarga devuelve un nuevo `CRect` que es igual a `CRect` aumenta en el número especificado de unidades de cada miembro del parámetro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#65](../../atl-mfc-shared/codesnippet/CPP/crect-class_24.cpp)]  
  
##  <a name="a-namecrectoperator-a-crectoperator--"></a><a name="crect__operator_-"></a>  CRect::operator-  
 Las primeras dos sobrecargas devuelven un `CRect` objeto que es igual a `CRect` desplazado por los desplazamientos indicados.  
  
```  
 
CRect operator-(
POINT   
point) const throw();

CRect operator-(
SIZE   
size) const throw();

CRect operator-(
LPCRECT   
lpRect) const throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 `point`  
 Un [PUNTO](../../mfc/reference/point-structure1.md) estructura o `CPoint` objeto que especifica el número de unidades para mover el valor devuelto.  
  
 `size`  
 Un [TAMAÑO](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura o `CSize` objeto que especifica el número de unidades para mover el valor devuelto.  
  
 `lpRect`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) estructura o `CRect` objeto que contiene el número de unidades para deflate cada lado del valor devuelto.  
  
### <a name="return-value"></a>Valor devuelto  
 El `CRect` resultante de mover o desinflándose `CRect` por el número de unidades especificadas en el parámetro.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro *x* y *y* (o `cx` y `cy`) se restan parámetros `CRect`posición de.  
  
 La tercera sobrecarga devuelve un nuevo `CRect` que es igual a `CRect` disminuye el número especificado de unidades de cada miembro del parámetro. Tenga en cuenta que esta sobrecarga funciona como [DeflateRect](#crect__deflaterect), no [SubtractRect](#crect__subtractrect).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#66](../../atl-mfc-shared/codesnippet/CPP/crect-class_25.cpp)]  
  
##  <a name="a-namecrectoperatorampa-crectoperator-amp"></a><a name="crect__operator__amp_"></a>  CRect::operator &amp;  
 Devuelve un `CRect` que es la intersección de `CRect` y *rect2*.  
  
```  
 
CRect operator&(
const RECT& 
rect2) const throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 *rect2*  
 Contiene un [RECT](../../mfc/reference/rect-structure1.md) o `CRect`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CRect` que es la intersección de `CRect` y *rect2*.  
  
### <a name="remarks"></a>Comentarios  
 La intersección es el rectángulo más grande que se encuentra en dos rectángulos.  
  
> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#crect__normalizerect) normalizar los rectángulos antes de llamar a esta función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#67](../../atl-mfc-shared/codesnippet/CPP/crect-class_26.cpp)]  
  
##  <a name="a-namecrectoperatorora-crectoperator-124"></a><a name="crect__operator__or"></a>  CRect::operator &#124;  
 Devuelve un `CRect` que es la unión de `CRect` y *rect2*.  
  
```  
 
CRect operator|(
const RECT& 
rect2) const throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 *rect2*  
 Contiene un [RECT](../../mfc/reference/rect-structure1.md) o `CRect`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CRect` que es la unión de `CRect` y *rect2*.  
  
### <a name="remarks"></a>Comentarios  
 La unión es el rectángulo más pequeño que contiene dos rectángulos.  
  
> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#crect__normalizerect) normalizar los rectángulos antes de llamar a esta función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#68](../../atl-mfc-shared/codesnippet/CPP/crect-class_27.cpp)]  
  
##  <a name="a-namecrectptinrecta-crectptinrect"></a><a name="crect__ptinrect"></a>  CRect::PtInRect  
 Determina si el punto especificado está dentro de `CRect`.  
  
```  
 
BOOL PtInRect(
POINT   
point) const throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 `point`  
 Contiene un [PUNTO](../../mfc/reference/point-structure1.md) estructura o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el punto está dentro de `CRect`; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Es un punto dentro de `CRect` Si se encuentra en el lado izquierdo o superior o está dentro de los cuatro lados. Un punto en el lado derecho o inferior está fuera de `CRect`.  
  
> [!NOTE]
>  Se debe normalizar el rectángulo o esta función puede producir un error. Puede llamar a [NormalizeRect](#crect__normalizerect) normalizar el rectángulo antes de llamar a esta función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#51](../../atl-mfc-shared/codesnippet/CPP/crect-class_28.cpp)]  
  
##  <a name="a-namecrectsetrecta-crectsetrect"></a><a name="crect__setrect"></a>  CRect::SetRect  
 Establece las dimensiones de `CRect` a las coordenadas especificadas.  
  
```  
 
    void SetRect(
    int 
    x1 ,  
    int 
    y1 ,  
    int 
    x2 ,  
    int 
    y2) throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 `x1`  
 Especifica la coordenada x de la esquina superior izquierda.  
  
 `y1`  
 Especifica la coordenada y de la esquina superior izquierda.  
  
 `x2`  
 Especifica la coordenada x de la esquina inferior derecha.  
  
 `y2`  
 Especifica la coordenada y de la esquina inferior derecha.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#52](../../atl-mfc-shared/codesnippet/CPP/crect-class_29.cpp)]  
  
##  <a name="a-namecrectsetrectemptya-crectsetrectempty"></a><a name="crect__setrectempty"></a>  CRect::SetRectEmpty  
 Hace que `CRect` un rectángulo null estableciendo todas las coordenadas en cero.  
  
```  
void SetRectEmpty() throw();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#53](../../atl-mfc-shared/codesnippet/CPP/crect-class_30.cpp)]  
  
##  <a name="a-namecrectsizea-crectsize"></a><a name="crect__size"></a>  CRect::Size  
 El `cx` y `cy` miembros del valor devuelto contienen el alto y ancho de `CRect`.  
  
```  
CSize Size() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que contiene el tamaño de `CRect`.  
  
### <a name="remarks"></a>Comentarios  
 El alto o el ancho puede ser negativo.  
  
> [!NOTE]
>  Se debe normalizar el rectángulo o esta función puede producir un error. Puede llamar a [NormalizeRect](#crect__normalizerect) normalizar el rectángulo antes de llamar a esta función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#54](../../atl-mfc-shared/codesnippet/CPP/crect-class_31.cpp)]  
  
##  <a name="a-namecrectsubtractrecta-crectsubtractrect"></a><a name="crect__subtractrect"></a>  CRect::SubtractRect  
 Hace que las dimensiones de la **CRect** igual que el resultado de restar `lpRectSrc2` desde `lpRectSrc1`.  
  
```  
 
    BOOL SubtractRect(
    LPCRECT 
    lpRectSrc1 ,  
    LPCRECT 
    lpRectSrc2) throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRectSrc1`  
 Apunta a la [RECT](../../mfc/reference/rect-structure1.md) estructura o `CRect` objeto desde el que se va a restar un rectángulo.  
  
 `lpRectSrc2`  
 Apunta a la `RECT` estructura o `CRect` objeto que se va a restar el rectángulo al que señala el `lpRectSrc1` parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 La resta es el rectángulo más pequeño que contiene todos los puntos de `lpRectScr1` que no están en la intersección de `lpRectScr1` y *lpRectScr2*.  
  
 El rectángulo especificado por `lpRectSrc1` no cambiarán si el rectángulo especificado por `lpRectSrc2` completamente no se superponga el rectángulo especificado por *lpRectSrc1* en al menos una de las direcciones x o y.  
  
 Por ejemplo, si `lpRectSrc1` fueron (10,10, 100,100) y `lpRectSrc2` fueron (50,50, 150,150), señala el rectángulo `lpRectSrc1` sería no cambia cuando se devuelve la función. Si `lpRectSrc1` fueron (10,10, 100,100) y `lpRectSrc2` fueron (50,10, 150,150), sin embargo, el rectángulo que apunta `lpRectSrc1` contendría las coordenadas (10,10, 50.100) cuando se devuelve la función.  
  
 `SubtractRect` no es el mismo que [operador -](#crect__operator_-) ni [operador-=](#crect__operator_-_eq). Ninguno de estos operadores nunca llama `SubtractRect`.  
  
> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#crect__normalizerect) normalizar los rectángulos antes de llamar a esta función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#55](../../atl-mfc-shared/codesnippet/CPP/crect-class_32.cpp)]  
  
##  <a name="a-namecrecttoplefta-crecttopleft"></a><a name="crect__topleft"></a>  CRect::TopLeft  
 Las coordenadas se devuelven como una referencia a un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto que se encuentra en `CRect`.  
  
```  
 
CPoint& TopLeft() throw();

const CPoint& TopLeft() const throw();

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Las coordenadas de la esquina superior izquierda del rectángulo.  
  
### <a name="remarks"></a>Comentarios  
 Puede utilizar esta función para obtener o establecer la esquina superior izquierda del rectángulo. Establecer la esquina mediante esta función en el lado izquierdo del operador de asignación.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CRect::CenterPoint](#crect__centerpoint).  
  
##  <a name="a-namecrectunionrecta-crectunionrect"></a><a name="crect__unionrect"></a>  CRect::UnionRect  
 Hace que las dimensiones de `CRect` igual que la unión de los rectángulos de origen de dos.  
  
```  
 
    BOOL UnionRect(
    LPCRECT 
    lpRect1 ,  
    LPCRECT 
    lpRect2) throw();

 
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect1`  
 Apunta a un [RECT](../../mfc/reference/rect-structure1.md) o `CRect` que contiene un rectángulo de origen.  
  
 `lpRect2`  
 Apunta a un `RECT` o `CRect` que contiene un rectángulo de origen.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la unión no está vacía; 0 si la unión está vacía.  
  
### <a name="remarks"></a>Comentarios  
 La unión es el rectángulo más pequeño que contiene dos rectángulos de origen.  
  
 Windows pasa por alto las dimensiones de un rectángulo vacío; es decir, un rectángulo que no tiene alto o sin ancho.  
  
> [!NOTE]
>  Se deben normalizar los rectángulos o esta función puede producir un error. Puede llamar a [NormalizeRect](#crect__normalizerect) normalizar los rectángulos antes de llamar a esta función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#56](../../atl-mfc-shared/codesnippet/CPP/crect-class_33.cpp)]  
  
##  <a name="a-namecrectwidtha-crectwidth"></a><a name="crect__width"></a>  CRect::Width  
 Calcula el ancho de `CRect` restando el valor de la izquierda desde el valor correcto.  
  
```  
int Width() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho de `CRect`.  
  
### <a name="remarks"></a>Comentarios  
 El ancho puede ser negativo.  
  
> [!NOTE]
>  Se debe normalizar el rectángulo o esta función puede producir un error. Puede llamar a [NormalizeRect](#crect__normalizerect) normalizar el rectángulo antes de llamar a esta función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATLMFC_Utilities#57](../../atl-mfc-shared/codesnippet/CPP/crect-class_34.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CPoint](../../atl-mfc-shared/reference/cpoint-class.md)   
 [Clase CSize](../../atl-mfc-shared/reference/csize-class.md)   
 [RECT](../../mfc/reference/rect-structure1.md)

