---
title: Clase CFormView
ms.date: 11/04/2016
f1_keywords:
- CFormView
- AFXEXT/CFormView
- AFXEXT/CFormView::CFormView
- AFXEXT/CFormView::IsInitDlgCompleted
helpviewer_keywords:
- CFormView [MFC], CFormView
- CFormView [MFC], IsInitDlgCompleted
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
ms.openlocfilehash: a9b897c661731878f0bf78c9d04ae7c4ba28cd42
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373797"
---
# <a name="cformview-class"></a>Clase CFormView

La clase base utilizada para las vistas de formulario.

## <a name="syntax"></a>Sintaxis

```
class CFormView : public CScrollView
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CFormView::CFormView](#cformview)|Construye un objeto `CFormView`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|Se usa para la sincronización durante la inicialización.|

## <a name="remarks"></a>Observaciones

Una vista de formulario es esencialmente una vista que contiene controles que se disponen en función de un recurso de plantilla de cuadro de diálogo. Use `CFormView` si quiere usar formularios en la aplicación. Estas vistas admiten el desplazamiento, según sea necesario, mediante la funcionalidad [CScrollView.](../../mfc/reference/cscrollview-class.md)

Al crear una aplicación [basada en formularios](../../mfc/reference/creating-a-forms-based-mfc-application.md), puede `CFormView`basar su clase de vista en , convirtiéndola en una aplicación basada en formularios.

También puede insertar nuevos temas de [formulario](../../mfc/form-views-mfc.md) en aplicaciones basadas en vista de documento. Aunque la aplicación no admitía formularios inicialmente, Visual C++ agregará automáticamente esta compatibilidad al insertar un formulario nuevo.

El Asistente para aplicaciones MFC y el comando Agregar clase son los métodos preferidos para crear aplicaciones basadas en formularios. Si necesita crear una aplicación basada en formularios sin usar estos métodos, consulte [Creación de una aplicación basada en formularios](../../mfc/reference/creating-a-forms-based-mfc-application.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

`CFormView`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

## <a name="cformviewcformview"></a><a name="cformview"></a>CFormView::CFormView

Construye un objeto `CFormView`.

```
CFormView(LPCTSTR lpszTemplateName);
CFormView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parámetros

*lpszTemplateName*<br/>
Contiene una cadena terminada en null que es el nombre de un recurso de plantilla de cuadro de diálogo.

*nIDTemplate*<br/>
Contiene el número de identificador de un recurso de plantilla de cuadro de diálogo.

### <a name="remarks"></a>Observaciones

Al crear un objeto de un `CFormView`tipo derivado de , invoque uno de los constructores para crear el objeto de vista e identificar el recurso de cuadro de diálogo en el que se basa la vista. Puede identificar el recurso por nombre (pasar una cadena como argumento al constructor) o por su identificador (pasar un entero sin signo como argumento).

La ventana de vista de formulario `CWnd::Create` y los controles secundarios no se crean hasta que se llama. `CWnd::Create`es llamado por el marco de trabajo como parte del proceso de creación de documentos y vistas, que está impulsado por la plantilla de documento.

> [!NOTE]
> La clase derivada *debe* proporcionar su propio constructor. En el constructor, invoque el constructor, `CFormView::CFormView`, con el nombre de recurso o el identificador como argumento como se muestra en la información general de la clase anterior.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]

[!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]

## <a name="cformviewisinitdlgcompleted"></a><a name="isinitdlgcompleted"></a>CFormView::IsInitDlgCompleted

Usado por MFC para garantizar que la inicialización se complete antes de llevar a cabo otras operaciones.

```
BOOL IsInitDlgCompleted() const;
```

### <a name="return-value"></a>Valor devuelto

True si se ha completado la función de inicialización para este cuadro de diálogo.

## <a name="see-also"></a>Consulte también

[EJEMPLO de MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CScrollView (clase)](../../mfc/reference/cscrollview-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CDialog](../../mfc/reference/cdialog-class.md)<br/>
[CScrollView (clase)](../../mfc/reference/cscrollview-class.md)
