---
title: Clase CStatic | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStatic
dev_langs:
- C++
helpviewer_keywords:
- enhanced metafiles
- cursors, displaying
- static controls
- controls [MFC], static
- icons, displaying
- CStatic class
- enhanced metafiles, displaying
- bitmaps, displaying
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
caps.latest.revision: 21
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 0209fad1b84b782cdec7927cb5a04e9bb3083d64
ms.lasthandoff: 02/24/2017

---
# <a name="cstatic-class"></a>Clase CStatic
Proporciona la funcionalidad de un control estático de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CStatic : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CStatic::CStatic](#cstatic)|Construye un objeto `CStatic`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CStatic::Create](#create)|Crea el control estático de Windows y lo adjunta a la `CStatic` objeto.|  
|[CStatic::DrawItem](#drawitem)|Invalidación para dibujar un control estático dibujado por el propietario.|  
|[CStatic::GetBitmap](#getbitmap)|Recupera el identificador del mapa de bits establecido previamente con [SetBitmap](#setbitmap).|  
|[CStatic::GetCursor](#getcursor)|Recupera el identificador de la imagen del cursor establecido previamente con [SetCursor](#setcursor).|  
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Recupera el identificador del metarchivo mejorado establecido previamente con [SetEnhMetaFile](#setenhmetafile).|  
|[CStatic::GetIcon](#geticon)|Recupera el identificador del icono establecido previamente con [SetIcon](#seticon).|  
|[CStatic::SetBitmap](#setbitmap)|Especifica un mapa de bits que se mostrará en el control estático.|  
|[CStatic::SetCursor](#setcursor)|Especifica una imagen del cursor que se mostrará en el control estático.|  
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Especifica un metarchivo mejorado que se mostrará en el control estático.|  
|[CStatic::SetIcon](#seticon)|Especifica el icono que se muestra en el control estático.|  
  
## <a name="remarks"></a>Comentarios  
 Un control estático muestra una cadena de texto, cuadro, rectángulo, icono, cursor, mapa de bits o metarchivo mejorado. Puede utilizar para etiquetar, cuadro o separar otros controles. Un control estático normalmente no tome ninguna entrada y no proporciona ningún resultado; Sin embargo, puede notificar a su elemento primario de clics del mouse si se ha creado con **SS_NOTIFY** estilo.  
  
 Crear un control estático en dos pasos. En primer lugar, llame al constructor para construir la `CStatic` objeto, a continuación, llame a la [crear](#create) función de miembro para crear el control estático y adjuntarlo a la `CStatic` objeto.  
  
 Si crea un `CStatic` objeto dentro de un cuadro de diálogo (a través de un recurso de cuadro de diálogo), el `CStatic` objeto se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.  
  
 Si crea un `CStatic` de objeto dentro de una ventana, puede que también necesite destruirlo. Un `CStatic` automáticamente se destruye el objeto creado en la pila en una ventana. Si crea el `CStatic` objeto en el montón mediante el uso de la **nueva** función, se debe llamar a **eliminar** en el objeto destruirla cuando haya terminado con él.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatic`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="a-namecreatea--cstaticcreate"></a><a name="create"></a>CStatic::Create  
 Crea el control estático de Windows y lo adjunta a la `CStatic` objeto.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszText,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID = 0xffff);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszText`  
 Especifica el texto que se va a colocar en el control. Si **NULL**, no estará visible.  
  
 `dwStyle`  
 Especifica el estilo de ventana del control estático. Aplicar cualquier combinación de [estilos de control estático](../../mfc/reference/static-styles.md) al control.  
  
 `rect`  
 Especifica la posición y el tamaño del control estático. Puede ser un `RECT` estructura o un `CRect` objeto.  
  
 `pParentWnd`  
 Especifica la `CStatic` ventana primaria, normalmente un `CDialog` objeto. No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador del control. del control estático  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Construir un `CStatic` objeto en dos pasos. En primer lugar, llame al constructor de `CStatic`y, a continuación, llame a **crear**, que crea el control estático de Windows y lo adjunta a la `CStatic` objeto.  
  
 Aplique el siguiente [estilos de ventana](../../mfc/reference/window-styles.md) a un control estático:  
  
- **WS_CHILD** siempre  
  
- **WS_VISIBLE** normalmente  
  
- **WS_DISABLED** rara vez  
  
 Si va a mostrar un mapa de bits, el cursor, el icono o el metarchivo en el control estático, debe aplicar uno de los siguientes [estilos estáticos](../../mfc/reference/static-styles.md):  
  
- **SS_BITMAP** utilizar este estilo para los mapas de bits.  
  
- **SS_ICON** utilizar este estilo para iconos y cursores.  
  
- **SS_ENHMETAFILE** utilizar este estilo de metarchivos mejorados.  
  
 Para los cursores, mapas de bits o iconos, también puede usar el siguiente estilo:  
  
- **SS_CENTERIMAGE** utilizar para centrar la imagen en el control estático.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[1 NVC_MFC_CStatic](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]  
  
##  <a name="a-namecstatica--cstaticcstatic"></a><a name="cstatic"></a>CStatic::CStatic  
 Construye un objeto `CStatic`.  
  
```  
CStatic();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic&#2;](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]  
  
##  <a name="a-namedrawitema--cstaticdrawitem"></a><a name="drawitem"></a>CStatic::DrawItem  
 Llamado por el marco para dibujar un control estático dibujado por el propietario.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDrawItemStruct`  
 Un puntero a un [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) estructura. La estructura contiene información sobre el elemento que se va a dibujar y el tipo de dibujo necesario.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para implementar el dibujo para dibujar un **CStatic** objeto (el control tiene el estilo **SS_OWNERDRAW**).  
  
##  <a name="a-namegetbitmapa--cstaticgetbitmap"></a><a name="getbitmap"></a>CStatic::GetBitmap  
 Obtiene el identificador del mapa de bits, establecido previamente con [SetBitmap](#setbitmap), que está asociado a `CStatic`.  
  
```  
HBITMAP GetBitmap() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el mapa de bits actual o **NULL** si no se ha establecido ningún mapa de bits.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic&3;](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]  
  
##  <a name="a-namegetcursora--cstaticgetcursor"></a><a name="getcursor"></a>CStatic::GetCursor  
 Obtiene el identificador del cursor, establecido previamente con [SetCursor](#setcursor), que está asociado a `CStatic`.  
  
```  
HCURSOR GetCursor();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el cursor actual, o **NULL** si no se ha establecido ningún cursor.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic Nº&4;](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]  
  
##  <a name="a-namegetenhmetafilea--cstaticgetenhmetafile"></a><a name="getenhmetafile"></a>CStatic::GetEnhMetaFile  
 Obtiene el identificador del metarchivo mejorado, establecido previamente con [SetEnhMetafile](#setenhmetafile), que está asociado a `CStatic`.  
  
```  
HENHMETAFILE GetEnhMetaFile() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de metarchivo mejorado actual, o **NULL** si no se ha establecido ningún metarchivo mejorado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic&#5;](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]  
  
##  <a name="a-namegeticona--cstaticgeticon"></a><a name="geticon"></a>CStatic::GetIcon  
 Obtiene el identificador del icono, establecido previamente con [SetIcon](#seticon), que está asociado a `CStatic`.  
  
```  
HICON GetIcon() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el icono actual, o **NULL** si no se ha establecido ningún icono.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic Nº&6;](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]  
  
##  <a name="a-namesetbitmapa--cstaticsetbitmap"></a><a name="setbitmap"></a>CStatic::SetBitmap  
 Asocia un nuevo mapa de bits con el control estático.  
  
```  
HBITMAP SetBitmap(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>Parámetros  
 `hBitmap`  
 Identificador del mapa de bits para dibujar en el control estático.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del mapa de bits que se asoció anteriormente con el control estático, o `NULL` si no estaba asociado con el control estático ningún mapa de bits.  
  
### <a name="remarks"></a>Comentarios  
 El mapa de bits se dibujarán automáticamente en el control estático. De forma predeterminada, se dibujará en la esquina superior izquierda y el control estático se ajustará al tamaño del mapa de bits.  
  
 Puede utilizar distintos de ventana y estilos de control estático, incluida ésta:  
  
-   SS_BITMAP utilizar este estilo siempre para los mapas de bits.  
  
-   Uso de SS_CENTERIMAGE para centrar la imagen en el control estático. Si la imagen es mayor que el control estático, se recortará. Si es menor que el control estático, el espacio vacío que rodea la imagen se rellenará con el color del píxel de la esquina superior izquierda del mapa de bits.  
  
-   MFC proporciona la clase `CBitmap`, que puede utilizar una vez más con una imagen de mapa de bits que llame a Win32 funcione `LoadBitmap`. `CBitmap`, que contiene un tipo de objeto GDI, se utiliza a menudo en cooperación con `CStatic`, que es un `CWnd` clase que se utiliza para mostrar un objeto gráfico como un control estático.  
  
 `CImage`es una clase ATL y MFC que permite más fácil trabajar con mapas de bits independientes del dispositivo (DIB). Para obtener más información, consulte [CImage (clase)](../../atl-mfc-shared/reference/cimage-class.md).  
  
-   Uso habitual consiste en dar `CStatic::SetBitmap` un objeto GDI que es devuelto por el operador HBITMAP de un `CBitmap` o `CImage` objeto. El código para hacer esto es similar a la siguiente línea.  
  
```  
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```  
En el ejemplo siguiente se crean dos `CStatic` objetos del montón. A continuación, carga uno con un mapa de bits del sistema con `CBitmap::LoadOEMBitmap` y el otro en un archivo utilizando `CImage::Load`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic&3;](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]  
  
##  <a name="a-namesetcursora--cstaticsetcursor"></a><a name="setcursor"></a>CStatic::SetCursor  
 Asocia una nueva imagen de cursor con el control estático.  
  
```  
HCURSOR SetCursor(HCURSOR hCursor);
```  
  
### <a name="parameters"></a>Parámetros  
 `hCursor`  
 Identificador del cursor para dibujar en el control estático.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del cursor asociado anteriormente con el control estático, o **NULL** si ningún cursor estaba asociado con el control estático.  
  
### <a name="remarks"></a>Comentarios  
 El cursor se dibujarán automáticamente en el control estático. De forma predeterminada, se dibujará en la esquina superior izquierda y el control estático se ajustará al tamaño del cursor.  
  
 Puede utilizar distintos de ventana y estilos de control estático, incluidos los siguientes:  
  
- **SS_ICON** utilizar este estilo siempre para iconos y cursores.  
  
- **SS_CENTERIMAGE** uso para centrar en el control estático. Si la imagen es mayor que el control estático, se recortará. Si es menor que el control estático, el espacio vacío que rodea la imagen se rellenará con el color de fondo del control estático.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic Nº&4;](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]  
  
##  <a name="a-namesetenhmetafilea--cstaticsetenhmetafile"></a><a name="setenhmetafile"></a>CStatic::SetEnhMetaFile  
 Asocia el control estático de una nueva imagen de metarchivo mejorado.  
  
```  
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```  
  
### <a name="parameters"></a>Parámetros  
 `hMetaFile`  
 Identificador del metarchivo mejorado para dibujar en el control estático.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del metarchivo mejorado asociado anteriormente con el control estático, o **NULL** si ningún metarchivo mejorado estaba asociado con el control estático.  
  
### <a name="remarks"></a>Comentarios  
 Metarchivo mejorado se dibujarán automáticamente en el control estático. Metarchivo mejorado se escala para ajustarse al tamaño del control estático.  
  
 Puede utilizar distintos de ventana y estilos de control estático, incluidos los siguientes:  
  
- **SS_ENHMETAFILE** utilizar este estilo siempre para metarchivos mejorados.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic&#5;](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]  
  
##  <a name="a-nameseticona--cstaticseticon"></a><a name="seticon"></a>CStatic::SetIcon  
 Asocia el control estático de una nueva imagen de icono.  
  
```  
HICON SetIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>Parámetros  
 `hIcon`  
 Identificador del icono para dibujar en el control estático.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del icono asociado anteriormente con el control estático, o **NULL** si no hay ningún icono estaba asociado con el control estático.  
  
### <a name="remarks"></a>Comentarios  
 El icono se dibujarán automáticamente en el control estático. De forma predeterminada, se dibujará en la esquina superior izquierda y el control estático se ajustará al tamaño del icono.  
  
 Puede utilizar distintos de ventana y estilos de control estático, incluidos los siguientes:  
  
- **SS_ICON** utilizar este estilo siempre para iconos y cursores.  
  
- **SS_CENTERIMAGE** uso para centrar en el control estático. Si la imagen es mayor que el control estático, se recortará. Si es menor que el control estático, el espacio vacío que rodea la imagen se rellenará con el color de fondo del control estático.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic Nº&6;](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [CButton (clase)](../../mfc/reference/cbutton-class.md)   
 [CComboBox (clase)](../../mfc/reference/ccombobox-class.md)   
 [Clase CEdit](../../mfc/reference/cedit-class.md)   
 [CListBox (clase)](../../mfc/reference/clistbox-class.md)   
 [Clase CScrollBar](../../mfc/reference/cscrollbar-class.md)   
 [CDialog (clase)](../../mfc/reference/cdialog-class.md)

