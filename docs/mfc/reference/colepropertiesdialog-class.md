---
title: Clase COlePropertiesDialog | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::DoModal
- AFXODLGS/COlePropertiesDialog::OnApplyScale
- AFXODLGS/COlePropertiesDialog::m_gp
- AFXODLGS/COlePropertiesDialog::m_lp
- AFXODLGS/COlePropertiesDialog::m_op
- AFXODLGS/COlePropertiesDialog::m_psh
- AFXODLGS/COlePropertiesDialog::m_vp
dev_langs:
- C++
helpviewer_keywords:
- OLE Object Properties dialog box
- Object Properties dialog box
- dialog boxes, OLE
- OLE documents, modifying properties
- property pages, OLE
- COlePropertiesDialog class
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
caps.latest.revision: 23
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 1a53c1e65504049e35fdec8065de279ca41fe342
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="colepropertiesdialog-class"></a>Clase COlePropertiesDialog
Encapsula el cuadro de diálogo Propiedades de objeto de OLE común de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COlePropertiesDialog : public COleDialog  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|Construye un objeto `COlePropertiesDialog`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COlePropertiesDialog::DoModal](#domodal)|Muestra el cuadro de diálogo y permite al usuario realizar una selección.|  
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|Lo llama el marco de trabajo cuando ha cambiado la escala de los elementos de documento.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COlePropertiesDialog::m_gp](#m_gp)|Una estructura que se utiliza para inicializar la página "General" de un `COlePropertiesDialog` objeto.|  
|[COlePropertiesDialog::m_lp](#m_lp)|Una estructura que se utiliza para inicializar la página de "Vínculo" de un `COlePropertiesDialog` objeto.|  
|[COlePropertiesDialog::m_op](#m_op)|Una estructura usada para inicializar el `COlePropertiesDialog` objeto.|  
|[COlePropertiesDialog::m_psh](#m_psh)|Una estructura usada para agregar páginas de propiedades personalizadas adicionales.|  
|[COlePropertiesDialog::m_vp](#m_vp)|Una estructura que se utiliza para personalizar la página de "Vista" de un `COlePropertiesDialog` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Cuadros de diálogo comunes de propiedades del objeto OLE proporcionan una manera sencilla de mostrar y modificar las propiedades de un elemento de documento OLE de manera coherente con los estándares de Windows. Estas propiedades incluyen, entre otros, información sobre el archivo representado por el elemento de documento, opciones para mostrar el icono y la escala de la imagen y la información en el vínculo del elemento (si el elemento está vinculado).  
  
 Para usar un `COlePropertiesDialog` objeto, primero cree el objeto utilizando el `COlePropertiesDialog` constructor. Después de que se ha construido el cuadro de diálogo, llame a la `DoModal` función de miembro para mostrar el cuadro de diálogo y permitir al usuario modificar las propiedades del elemento. `DoModal`Devuelve si el usuario selecciona Aceptar ( **IDOK**) o en Cancelar ( **IDCANCEL**) botón. Además de los botones Aceptar y Cancelar, hay un botón Aplicar. Cuando el usuario selecciona aplicar, los cambios realizados en las propiedades de los elementos de documento se aplican al elemento y su imagen se actualiza automáticamente, pero permanece activa.  
  
 El [m_psh](#m_psh) miembro de datos es un puntero a un **PROPSHEETHEADER** estructura y en la mayoría de los casos no necesitará tener acceso a él de forma explícita. Una excepción es cuando tiene páginas de propiedades adicionales más allá de las páginas de General, ver y vincular de forma predeterminada. En este caso, puede modificar el `m_psh` miembro de datos para incluir sus páginas personalizadas antes de llamar a la `DoModal` función miembro.  
  
 Para obtener más información sobre los cuadros de diálogo OLE, vea el artículo [cuadros de diálogo en OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePropertiesDialog`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxodlgs.h  
  
##  <a name="colepropertiesdialog"></a>COlePropertiesDialog::COlePropertiesDialog  
 Crea un objeto `COlePropertiesDialog`.  
  
```  
COlePropertiesDialog(
    COleClientItem* pItem,  
    UINT nScaleMin = 10,  
    UINT nScaleMax = 500,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pItem`  
 Puntero al elemento de documento cuyas propiedades se tiene acceso.  
  
 *nScaleMin*  
 Porcentaje mínimo de escala de la imagen de elemento de documento.  
  
 *nScaleMax*  
 Ajuste de escala en porcentaje para la imagen de elemento de documento como máximo.  
  
 `pParentWnd`  
 Puntero al elemento primario o el propietario del cuadro de diálogo.  
  
### <a name="remarks"></a>Comentarios  
 Derive la clase de cuadro de diálogo de propiedades del objeto OLE común de `COlePropertiesDialog` para implementar el ajuste de escala para los elementos de documento. Los cuadros de diálogo que se implementa en una instancia de esta clase no admitirá la escala de los elementos de documento.  
  
 De forma predeterminada, el cuadro de diálogo de propiedades del objeto OLE común tiene tres páginas de forma predeterminada:  
  
-   General  
  
     Esta página contiene información del sistema para el archivo representado por el elemento de documento seleccionado. Desde esta página, el usuario puede convertir el elemento seleccionado a otro tipo.  
  
-   Ver  
  
     Esta página contiene las opciones para mostrar el elemento, cambiar el icono y cambiar la escala de la imagen.  
  
-   Link  
  
     Esta página contiene opciones para cambiar la ubicación del elemento vinculado y actualizar el elemento vinculado. Desde esta página, el usuario puede romper el vínculo del elemento seleccionado.  
  
 Para agregar páginas más allá de los proporcionados de manera predeterminada, modifique la [m_psh](#m_psh) variable miembro antes de salir del constructor de la `COlePropertiesDialog`-clase derivada. Se trata de una implementación avanzada de la `COlePropertiesDialog` constructor.  
  
##  <a name="domodal"></a>COlePropertiesDialog::DoModal  
 Llame a esta función miembro para mostrar el cuadro de diálogo de propiedades del objeto OLE común de Windows y permite al usuario ver o cambiar las distintas propiedades de los elementos de documento.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valor devuelto  
 **IDOK** o **IDCANCEL** si es correcto; en caso contrario, 0. **IDOK** y **IDCANCEL** son constantes que indican si el usuario selecciona el botón Aceptar o en Cancelar.  
  
 Si **IDCANCEL** se devuelve, se pueden llamar a las ventanas [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) función para determinar si se produjo un error.  
  
##  <a name="m_gp"></a>COlePropertiesDialog::m_gp  
 Una estructura de tipo [OLEUIGNRLPROPS](http://msdn.microsoft.com/library/windows/desktop/ms687297), que se usa para inicializar la página General del cuadro de diálogo Propiedades del objeto OLE.  
  
```  
OLEUIGNRLPROPS m_gp;  
```  
  
### <a name="remarks"></a>Comentarios  
 Esta página muestra el tipo y el tamaño de una incrustación y concede al usuario acceso al cuadro de diálogo convertir. Esta página también muestra el destino del vínculo si el objeto es un vínculo.  
  
 Para obtener más información sobre la **OLEUIGNRLPROPS** estructura, vea la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="m_lp"></a>COlePropertiesDialog::m_lp  
 Una estructura de tipo [OLEUILINKPROPS](http://msdn.microsoft.com/library/windows/desktop/ms680735), que se usa para inicializar la página de vínculo del cuadro de diálogo Propiedades del objeto OLE.  
  
```  
OLEUILINKPROPS m_lp;  
```  
  
### <a name="remarks"></a>Comentarios  
 Esta página muestra la ubicación del elemento vinculado y permite al usuario actualice o se ha interrumpido, el vínculo al elemento.  
  
 Para obtener más información sobre la **OLEUILINKPROPS** estructura, vea la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="m_op"></a>COlePropertiesDialog::m_op  
 Una estructura de tipo [OLEUIOBJECTPROPS](http://msdn.microsoft.com/library/windows/desktop/ms687199), que se usa para inicializar el cuadro de diálogo de propiedades del objeto OLE común.  
  
```  
OLEUIOBJECTPROPS m_op;  
```  
  
### <a name="remarks"></a>Comentarios  
 Esta estructura contiene a miembros que se utilizan para inicializar las páginas generales, vínculo y vista.  
  
 Para obtener más información, consulte el **OLEUIOBJECTPROPS** y [OLEUILINKPROPS](http://msdn.microsoft.com/library/windows/desktop/ms680735) las estructuras de los [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="m_psh"></a>COlePropertiesDialog::m_psh  
 Una estructura de tipo [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546), cuyos miembros almacenan las características del objeto de cuadro de diálogo.  
  
```  
PROPSHEETHEADER m_psh;  
```  
  
### <a name="remarks"></a>Comentarios  
 Después de crear un `COlePropertiesDialog` objeto, puede usar `m_psh` para establecer varios aspectos del cuadro de diálogo antes de llamar a la `DoModal` función miembro.  
  
 Si modifica el `m_psh` miembro de datos directamente, deberá reemplazar cualquier comportamiento predeterminado.  
  
 Para obtener más información sobre la **PROPSHEETHEADER** estructura, vea la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="m_vp"></a>COlePropertiesDialog::m_vp  
 Una estructura de tipo [OLEUIVIEWPROPS](http://msdn.microsoft.com/library/windows/desktop/ms693751), que se usa para inicializar la página de vista del cuadro de diálogo Propiedades del objeto OLE.  
  
```  
OLEUIVIEWPROPS m_vp;  
```  
  
### <a name="remarks"></a>Comentarios  
 Esta página permite al usuario alternar entre "contenido" y "icono" vistas del objeto y cambiar su escala dentro del contenedor. También permite al usuario acceso al cuadro de diálogo Cambiar icono cuando el objeto se muestra como un icono.  
  
 Para obtener más información sobre la **OLEUIVIEWPROPS** estructura, vea la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="onapplyscale"></a>COlePropertiesDialog::OnApplyScale  
 Lo llama el marco de trabajo cuando ha cambiado el valor de escala y se ha seleccionado Aceptar o aplicar.  
  
```  
virtual BOOL OnApplyScale(
    COleClientItem* pItem,  
    int nCurrentScale,  
    BOOL bRelativeToOrig);
```  
  
### <a name="parameters"></a>Parámetros  
 `pItem`  
 Puntero al elemento de documento cuyas propiedades se tiene acceso.  
  
 `nCurrentScale`  
 Valor numérico de la escala del cuadro de diálogo.  
  
 *bRelativeToOrig*  
 Indica si la escala se aplica al tamaño original de los elementos de documento.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se administran; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no hace nada. Se debe reemplazar esta función para habilitar los controles de escala.  
  
> [!NOTE]
>  Antes de mostrar el cuadro de diálogo de propiedades del objeto OLE común, el marco de trabajo llama a esta función con un **NULL** para `pItem` y a - 1 para `nCurrentScale`. Esto se hace para determinar si los controles de escala deben estar habilitados.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MFC CIRC](../../visual-cpp-samples.md)   
 [Clase COleDialog](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clase COleDialog](../../mfc/reference/coledialog-class.md)   
 [CPropertyPage (clase)](../../mfc/reference/cpropertypage-class.md)

