---
title: "CMFCMaskedEdit Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCMaskedEdit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCMaskedEdit class"
  - "CMFCMaskedEdit constructor"
ms.assetid: 13b1a645-2d5d-4c37-8599-16d5003f23a5
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CMFCMaskedEdit Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCMaskedEdit` admite un control de edición enmascarado, que valida los datos proporcionados por el usuario en una máscara y muestra los resultados validados como una plantilla.  
  
## Sintaxis  
  
```  
class CMFCMaskedEdit : public CEdit  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCMaskedEdit::CMFCMaskedEdit`|Constructor predeterminado.|  
|`CMFCMaskedEdit::~CMFCMaskedEdit`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCMaskedEdit::DisableMask](../Topic/CMFCMaskedEdit::DisableMask.md)|Deshabilita validar los datos proporcionados por el usuario.|  
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](../Topic/CMFCMaskedEdit::EnableGetMaskedCharsOnly.md)|Especifica si el método de `GetWindowText` recupera únicamente caracteres enmascarados.|  
|[CMFCMaskedEdit::EnableMask](../Topic/CMFCMaskedEdit::EnableMask.md)|Inicializa el control de edición enmascarado.|  
|[CMFCMaskedEdit::EnableSelectByGroup](../Topic/CMFCMaskedEdit::EnableSelectByGroup.md)|Especifica si el control de edición enmascarado selecciona los grupos concretos de datos proporcionados por el usuario, o todos los datos proporcionados por el usuario.|  
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](../Topic/CMFCMaskedEdit::EnableSetMaskedCharsOnly.md)|Especifica si el texto se validará con únicamente caracteres enmascarados, o con la máscara entera.|  
|`CMFCMaskedEdit::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CMFCMaskedEdit::GetWindowText](../Topic/CMFCMaskedEdit::GetWindowText.md)|Texto validado recupera del control de edición enmascarado.|  
|[CMFCMaskedEdit::SetValidChars](../Topic/CMFCMaskedEdit::SetValidChars.md)|Especifica una cadena de caracteres válido que el usuario puede especificar.|  
|[CMFCMaskedEdit::SetWindowText](../Topic/CMFCMaskedEdit::SetWindowText.md)|Muestra un indicador en el control de edición enmascarado.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCMaskedEdit::IsMaskedChar](../Topic/CMFCMaskedEdit::IsMaskedChar.md)|Llamado por el marco para validar el carácter especificado con el carácter correspondiente de la máscara.|  
  
## Comentarios  
 Realice los pasos siguientes para utilizar el control de `CMFCMaskedEdit` en su aplicación:  
  
 1.  Inserte un objeto de `CMFCMaskedEdit` en la clase de ventana.  
  
 2.  Llame al método de [CMFCMaskedEdit::EnableMask](../Topic/CMFCMaskedEdit::EnableMask.md) para especificar la máscara.  
  
 3.  Llame al método de [CMFCMaskedEdit::SetValidChars](../Topic/CMFCMaskedEdit::SetValidChars.md) para especificar la lista de caracteres válidos.  
  
 4.  Llame al método de [CMFCMaskedEdit::SetWindowText](../Topic/CMFCMaskedEdit::SetWindowText.md) para especificar el texto predeterminado para el control de edición enmascarado.  
  
 5.  Llame al método de [CMFCMaskedEdit::GetWindowText](../Topic/CMFCMaskedEdit::GetWindowText.md) para recuperar el texto validado.  
  
 Si no se llama a uno o varios métodos para inicializar la máscara, los caracteres válidos, y el texto del valor predeterminado, el control de edición enmascarado se comporta igual que el control edit estándar se comporta.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo configurar una máscara \(como un número de teléfono\) mediante el método de `EnableMask` para crear la máscara para que el control de edición enmascarado, el método de `SetValidChars` para especificar una cadena de caracteres válido que el usuario puede especificar, y el método de `SetWindowText` muestren un marcador en el control de edición enmascarado.  Este ejemplo forma parte de [nuevo ejemplo de Controles](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/CPP/cmfcmaskededit-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/CPP/cmfcmaskededit-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)  
  
## Requisitos  
 **encabezado:** afxmaskededit.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)