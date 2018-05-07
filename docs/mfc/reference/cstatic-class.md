---
title: Clase CStatic | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStatic
- AFXWIN/CStatic
- AFXWIN/CStatic::CStatic
- AFXWIN/CStatic::Create
- AFXWIN/CStatic::DrawItem
- AFXWIN/CStatic::GetBitmap
- AFXWIN/CStatic::GetCursor
- AFXWIN/CStatic::GetEnhMetaFile
- AFXWIN/CStatic::GetIcon
- AFXWIN/CStatic::SetBitmap
- AFXWIN/CStatic::SetCursor
- AFXWIN/CStatic::SetEnhMetaFile
- AFXWIN/CStatic::SetIcon
dev_langs:
- C++
helpviewer_keywords:
- CStatic [MFC], CStatic
- CStatic [MFC], Create
- CStatic [MFC], DrawItem
- CStatic [MFC], GetBitmap
- CStatic [MFC], GetCursor
- CStatic [MFC], GetEnhMetaFile
- CStatic [MFC], GetIcon
- CStatic [MFC], SetBitmap
- CStatic [MFC], SetCursor
- CStatic [MFC], SetEnhMetaFile
- CStatic [MFC], SetIcon
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d3b1a5dcfc8481727bffd8b80e0bb1b230d56ff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cstatic-class"></a>Clase CStatic
Proporciona la funcionalidad de un control estático de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CStatic : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStatic::CStatic](#cstatic)|Construye un objeto `CStatic`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStatic::Create](#create)|Crea el control estático de Windows y lo adjunta a la `CStatic` objeto.|  
|[CStatic::DrawItem](#drawitem)|Reemplace este valor para dibujar un control estático dibujado por el propietario.|  
|[CStatic::GetBitmap](#getbitmap)|Recupera el identificador del mapa de bits establecidos previamente con [SetBitmap](#setbitmap).|  
|[CStatic::GetCursor](#getcursor)|Recupera el identificador de la imagen del cursor establecido previamente con [SetCursor](#setcursor).|  
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Recupera el identificador del metarchivo mejorado establecido previamente con [SetEnhMetaFile](#setenhmetafile).|  
|[CStatic::GetIcon](#geticon)|Recupera el identificador del icono establecido previamente con [SetIcon](#seticon).|  
|[CStatic::SetBitmap](#setbitmap)|Especifica un mapa de bits que se mostrará en el control estático.|  
|[CStatic::SetCursor](#setcursor)|Especifica una imagen del cursor que se mostrará en el control estático.|  
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Especifica un metarchivo mejorado para mostrarse en el control estático.|  
|[CStatic::SetIcon](#seticon)|Especifica el icono que se muestra en el control estático.|  
  
## <a name="remarks"></a>Comentarios  
 Un control estático muestra una cadena de texto, cuadro, rectángulo, icono, cursor, mapa de bits o metarchivo mejorado. Se puede utilizar para etiquetar, cuadro o separado de otros controles. Un control estático normalmente no toma ninguna entrada y no proporciona ningún resultado; Sin embargo, puede notificar a su elemento primario de clics del mouse si se crea con **SS_NOTIFY** estilo.  
  
 Crear un control estático en dos pasos. En primer lugar, llame al constructor para construir el `CStatic` de objeto y después llamar a la [crear](#create) función de miembro para crear el control estático y adjuntarla a la `CStatic` objeto.  
  
 Si crea un `CStatic` objeto dentro de un cuadro de diálogo (a través de un recurso de cuadro de diálogo), el `CStatic` objeto se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.  
  
 Si crea un `CStatic` de objeto dentro de una ventana, puede que también necesite destruirlo. Un `CStatic` automáticamente se destruye el objeto creado en la pila dentro de una ventana. Si crea el `CStatic` objeto en el montón mediante el uso de la **nueva** función, se debe llamar a **eliminar** del objeto que se va a destruir cuando haya terminado con él.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatic`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="create"></a>  CStatic::Create  
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
 Especifica el estilo de ventana del control estático. Aplicar cualquier combinación de [estilos de control estático](../../mfc/reference/styles-used-by-mfc.md#static-styles) al control.  
  
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
  
 Aplique el siguiente [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) a un control estático:  
  
- **WS_CHILD** siempre  
  
- **WS_VISIBLE** normalmente  
  
- **WS_DISABLED** rara vez  
  
 Si se va a mostrar un mapa de bits, un cursor, un icono o un metarchivo en el control estático, debe aplicar uno de los siguientes [estilos estáticos](../../mfc/reference/styles-used-by-mfc.md#static-styles):  
  
- **SS_BITMAP** utilizar este estilo para los mapas de bits.  
  
- **SS_ICON** utilizar este estilo para iconos y cursores.  
  
- **SS_ENHMETAFILE** usar este estilo de metarchivo mejorado.  
  
 Para los cursores, mapas de bits o iconos, también puede usar el siguiente estilo:  
  
- **SS_CENTERIMAGE** utilice para centrar la imagen en el control estático.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]  
  
##  <a name="cstatic"></a>  CStatic::CStatic  
 Construye un objeto `CStatic`.  
  
```  
CStatic();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]  
  
##  <a name="drawitem"></a>  CStatic::DrawItem  
 Lo llama el marco de trabajo para dibujar un control estático dibujado por el propietario.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDrawItemStruct`  
 Un puntero a un [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) estructura. La estructura contiene información sobre el elemento que se va a dibujar y el tipo de dibujo necesaria.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función para implementar un dibujado por el propietario del dibujo **CStatic** objeto (el control tiene el estilo **SS_OWNERDRAW**).  
  
##  <a name="getbitmap"></a>  CStatic::GetBitmap  
 Obtiene el identificador del mapa de bits, establecido previamente con [SetBitmap](#setbitmap), que está asociado a `CStatic`.  
  
```  
HBITMAP GetBitmap() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el mapa de bits actual, o **NULL** si no se ha establecido ningún mapa de bits.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]  
  
##  <a name="getcursor"></a>  CStatic::GetCursor  
 Obtiene el identificador del cursor, establecido previamente con [SetCursor](#setcursor), que está asociado a `CStatic`.  
  
```  
HCURSOR GetCursor();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el cursor actual, o **NULL** si no se ha establecido ningún cursor.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]  
  
##  <a name="getenhmetafile"></a>  CStatic::GetEnhMetaFile  
 Obtiene el identificador del metarchivo mejorado, establecido previamente con [SetEnhMetafile](#setenhmetafile), que está asociado a `CStatic`.  
  
```  
HENHMETAFILE GetEnhMetaFile() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el metarchivo mejorado actual, o **NULL** si no se ha establecido ningún metarchivo mejorado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]  
  
##  <a name="geticon"></a>  CStatic::GetIcon  
 Obtiene el identificador del icono, establecido previamente con [SetIcon](#seticon), que está asociado a `CStatic`.  
  
```  
HICON GetIcon() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el sitio actual, o **NULL** si no se ha establecido ningún icono.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]  
  
##  <a name="setbitmap"></a>  CStatic::SetBitmap  
 Asocia un nuevo mapa de bits del control estático.  
  
```  
HBITMAP SetBitmap(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>Parámetros  
 `hBitmap`  
 Identificador del mapa de bits para dibujar en el control estático.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del mapa de bits que estaban asociado previamente con el control estático, o `NULL` si no estaba asociado con el control estático ningún mapa de bits.  
  
### <a name="remarks"></a>Comentarios  
 El mapa de bits se dibujarán automáticamente en el control estático. De forma predeterminada, se dibujará en la esquina superior izquierda y el control estático se ajustará al tamaño del mapa de bits.  
  
 Puede utilizar varias ventanas y estilos de control estático, incluidos los siguientes:  
  
-   SS_BITMAP usar siempre este estilo para los mapas de bits.  
  
-   Uso de SS_CENTERIMAGE para centrar la imagen en el control estático. Si la imagen es mayor que el control estático, se recortará. Si es menor que el control estático, se rellenará el espacio vacío alrededor de la imagen mediante el color del píxel de la esquina superior izquierda del mapa de bits.  
  
-   MFC proporciona la clase `CBitmap`, que puede usar una vez más con una imagen de mapa de bits que llame a Win32 funcionando `LoadBitmap`. `CBitmap`, que contiene un tipo de objeto GDI, se utiliza a menudo en cooperación con `CStatic`, que es un `CWnd` clase que se utiliza para mostrar un objeto gráfico como un control estático.  
  
 `CImage` es una clase ATL y MFC que le permite más fácil trabajar con mapas de bits independientes del dispositivo (DIB). Para obtener más información, consulte [CImage (clase)](../../atl-mfc-shared/reference/cimage-class.md).  
  
-   Uso habitual consiste en dar `CStatic::SetBitmap` un objeto GDI que es devuelto por el operador HBITMAP de un `CBitmap` o `CImage` objeto. El código para hacer esto es similar a la siguiente línea.  
  
```  
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```  
En el ejemplo siguiente se crea dos `CStatic` objetos del montón. A continuación, carga uno con un mapa de bits del sistema con `CBitmap::LoadOEMBitmap` y otro de un archivo mediante `CImage::Load`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]  
  
##  <a name="setcursor"></a>  CStatic::SetCursor  
 Asocia una nueva imagen de cursor con el control estático.  
  
```  
HCURSOR SetCursor(HCURSOR hCursor);
```  
  
### <a name="parameters"></a>Parámetros  
 `hCursor`  
 Identificador del cursor para dibujar en el control estático.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del cursor previamente asociado al control estático, o **NULL** si ningún cursor estaba asociado con el control estático.  
  
### <a name="remarks"></a>Comentarios  
 El cursor se dibujarán automáticamente en el control estático. De forma predeterminada, se dibujará en la esquina superior izquierda y el control estático se ajustará al tamaño del cursor.  
  
 Puede utilizar varias ventanas y estilos de control estático, incluidas las siguientes:  
  
- **SS_ICON** usan este estilo siempre para iconos y cursores.  
  
- **SS_CENTERIMAGE** uso para centrar en el control estático. Si la imagen es mayor que el control estático, se recortará. Si es menor que el control estático, se rellenará el espacio vacío alrededor de la imagen con el color de fondo del control estático.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]  
  
##  <a name="setenhmetafile"></a>  CStatic::SetEnhMetaFile  
 Asocia una nueva imagen de metarchivo mejorado el control estático.  
  
```  
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```  
  
### <a name="parameters"></a>Parámetros  
 `hMetaFile`  
 Identificador del metarchivo mejorado para dibujar en el control estático.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del metarchivo mejorado previamente asociado al control estático, o **NULL** si no hay ningún metarchivo mejorado estaba asociado con el control estático.  
  
### <a name="remarks"></a>Comentarios  
 Metarchivo mejorado se dibujarán automáticamente en el control estático. Metarchivo mejorado se escala para ajustarse al tamaño del control estático.  
  
 Puede utilizar varias ventanas y estilos de control estático, incluidas las siguientes:  
  
- **SS_ENHMETAFILE** usar siempre este estilo de metarchivo mejorado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]  
  
##  <a name="seticon"></a>  CStatic::SetIcon  
 Asocia una nueva imagen de icono del control estático.  
  
```  
HICON SetIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>Parámetros  
 `hIcon`  
 Identificador del icono que se va a dibujar en el control estático.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del icono previamente asociado al control estático, o **NULL** si ningún icono estaba asociado con el control estático.  
  
### <a name="remarks"></a>Comentarios  
 El icono se dibujarán automáticamente en el control estático. De forma predeterminada, se dibujará en la esquina superior izquierda y el control estático se ajustará al tamaño del icono.  
  
 Puede utilizar varias ventanas y estilos de control estático, incluidas las siguientes:  
  
- **SS_ICON** usan este estilo siempre para iconos y cursores.  
  
- **SS_CENTERIMAGE** uso para centrar en el control estático. Si la imagen es mayor que el control estático, se recortará. Si es menor que el control estático, se rellenará el espacio vacío alrededor de la imagen con el color de fondo del control estático.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Clase CButton](../../mfc/reference/cbutton-class.md)   
 [CComboBox (clase)](../../mfc/reference/ccombobox-class.md)   
 [Clase CEdit](../../mfc/reference/cedit-class.md)   
 [CListBox (clase)](../../mfc/reference/clistbox-class.md)   
 [Clase CScrollBar](../../mfc/reference/cscrollbar-class.md)   
 [CDialog (clase)](../../mfc/reference/cdialog-class.md)
