---
title: "COlePropertiesDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COlePropertiesDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COlePropertiesDialog class"
  - "cuadros de diálogo, OLE"
  - "Object Properties dialog box"
  - "OLE documents, modificar propiedades"
  - "OLE Object Properties dialog box"
  - "páginas de propiedades, OLE"
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# COlePropertiesDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula el cuadro de diálogo Propiedades común del objeto OLE de Windows.  
  
## Sintaxis  
  
```  
  
class COlePropertiesDialog : public COleDialog  
  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COlePropertiesDialog::COlePropertiesDialog](../Topic/COlePropertiesDialog::COlePropertiesDialog.md)|Crea un objeto `COlePropertiesDialog`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COlePropertiesDialog::DoModal](../Topic/COlePropertiesDialog::DoModal.md)|Muestra el cuadro de diálogo y permite que el usuario realice una selección.|  
|[COlePropertiesDialog::OnApplyScale](../Topic/COlePropertiesDialog::OnApplyScale.md)|Llamado por el marco cuando el ajuste de escala del elemento de documento ha cambiado.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COlePropertiesDialog::m\_gp](../Topic/COlePropertiesDialog::m_gp.md)|Una estructura utilizada para inicializar la página de “General” de un objeto de `COlePropertiesDialog` .|  
|[COlePropertiesDialog::m\_lp](../Topic/COlePropertiesDialog::m_lp.md)|Una estructura utilizada para inicializar la página “vínculo” de un objeto de `COlePropertiesDialog` .|  
|[COlePropertiesDialog::m\_op](../Topic/COlePropertiesDialog::m_op.md)|Una estructura usada para inicializar el objeto de `COlePropertiesDialog` .|  
|[COlePropertiesDialog::m\_psh](../Topic/COlePropertiesDialog::m_psh.md)|Una estructura utilizada para agregar páginas de propiedades personalizadas adicionales.|  
|[COlePropertiesDialog::m\_vp](../Topic/COlePropertiesDialog::m_vp.md)|Una estructura utilizada para personalizar la página “vista” de un objeto de `COlePropertiesDialog` .|  
  
## Comentarios  
 Los cuadros de diálogo de Propiedades comunes de objetos OLE proporcionan una manera fácil de mostrar y modificar las propiedades de un elemento OLE de una manera coherente con los estándares de Windows.  Estas propiedades incluyen, entre otros, información del archivo representado por el elemento de documento, opciones para mostrar el ajuste de escala de icono y la imagen, y la información del vínculo del elemento \(si se vincula el elemento\).  
  
 Para utilizar un objeto de `COlePropertiesDialog` , primero cree el objeto mediante el constructor de `COlePropertiesDialog` .  Una vez construido el cuadro de diálogo, llame a la función miembro de `DoModal` para mostrar el cuadro de diálogo y permite al usuario modificar cualquier propiedad del elemento.  `DoModal` devuelve si el usuario seleccionó OK \(**IDOK**\) o el botón cancelar \(**IDCANCEL**\).  Además de la ACEPTAR y de los botones Cancelar, hay un botón de aplicar.  Cuando el usuario selecciona aplique, los cambios realizados en las propiedades del elemento de documento se aplica al elemento y su imagen se actualiza automáticamente, pero permanece activo.  
  
 El miembro de datos de [m\_psh](../Topic/COlePropertiesDialog::m_psh.md) es un puntero a una estructura de **PROPSHEETHEADER** y, en la mayoría de los casos no necesitará tener acceso explícitamente.  Una excepción es cuando necesita las páginas de propiedades adicionales más allá del valor predeterminado General, ver, y enlaza las páginas.  En este caso, puede modificar el miembro de datos de `m_psh` para incluir las páginas personalizadas antes de llamar a la función miembro de `DoModal` .  
  
 Para obtener más información sobre los cuadros de diálogo de OLE, vea el artículo [Cuadros de diálogo de OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePropertiesDialog`  
  
## Requisitos  
 **encabezado:** afxodlgs.h  
  
## Vea también  
 [ejemplo CIRC de MFC](../../top/visual-cpp-samples.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [CPropertyPage Class](../../mfc/reference/cpropertypage-class.md)