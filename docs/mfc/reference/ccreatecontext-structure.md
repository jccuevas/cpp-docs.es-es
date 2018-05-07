---
title: Estructura de CCreateContext | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCreateContext
dev_langs:
- C++
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af6e81b9215aa6e7bc9e5f294a1d95aee4b51321
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="ccreatecontext-structure"></a>Estructura de CCreateContext
El marco de trabajo usa el `CCreateContext` estructura al crear las vistas que están asociadas a un documento y ventanas de marco.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct CCreateContext  
```  
  
## <a name="remarks"></a>Comentarios  
 `CCreateContext` es una estructura y no tiene una clase base.  
  
 Cuando se crea una ventana, los valores de esta estructura proporcionan la información utilizada para conectar los componentes de un documento a la vista de sus datos. Solo tiene que usar `CCreateContext` si va a reemplazar partes del proceso de creación.  
  
 Un `CCreateContext` estructura contiene punteros a la plantilla de documento, la ventana de marco, la vista y el documento. También contiene un puntero a un `CRuntimeClass` que identifica el tipo de vista para crear. La información de clase en tiempo de ejecución y el puntero del documento actual se utilizan para crear una nueva vista de forma dinámica. La siguiente tabla se sugiere cómo y cuándo cada `CCreateContext` podría utilizarse miembro:  
  
|Miembro|Tipo|¿Qué es|  
|------------|----------|--------------------|  
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass` de la nueva vista que se va a crear.|  
|`m_pCurrentDoc`|`CDocument*`|El documento existente que se asociará con la nueva vista.|  
|`m_pNewDocTemplate`|`CDocTemplate*`|La plantilla de documento asociada a la creación de una nueva ventana de marco MDI.|  
|`m_pLastView`|`CView*`|La vista original en el que se modelan vistas adicionales, como se muestra en la creación de vistas de la ventana divisora o la creación de una segunda vista en un documento.|  
|`m_pCurrentFrame`|`CFrameWnd*`|La ventana de marco en el que se modelan ventanas de marco adicionales, como se muestra en la creación de una segunda ventana de marco en un documento.|  
  
 Cuando una plantilla de documento crea un documento y sus componentes asociados, valida la información almacenada en el `CCreateContext` estructura. Por ejemplo, no se debe crear una vista para un documento no existe.  
  
> [!NOTE]
>  Todos los punteros de `CCreateContext` son opcionales y pueden ser `NULL` si ha especificado o desconocido.  
  
 `CCreateContext` se utiliza por las funciones de miembro aparecen bajo "Vea también". Si tiene previsto reemplazarlos, consulte las descripciones de estas funciones para obtener información específica.  
  
 Estas son algunas directrices generales:  
  
-   Cuando se pasa como un argumento para la creación de ventana, como en `CWnd::Create`, `CFrameWnd::Create`, y `CFrameWnd::LoadFrame`, el contexto de crear especifica qué opciones que se debe conectar a la nueva ventana. Para la mayoría de las ventanas, la estructura completa es opcional y un `NULL` se puede pasar el puntero.  
  
-   Para las funciones miembro reemplazables, como `CFrameWnd::OnCreateClient`, el `CCreateContext` argumento es opcional.  
  
-   Para las funciones de miembro implicadas en la vista creación, debe proporcionar suficiente información para crear la vista. Por ejemplo, para la primera vista de una ventana divisora, debe proporcionar la información de la clase de vista y el documento actual.  
  
 En general, si utiliza los valores predeterminados de framework, puede omitir `CCreateContext`. Si intentas modificaciones más avanzadas, el código de origen de la biblioteca Microsoft Foundation Class o los programas de ejemplo, como VIEWEX, le ayudará. Si ha olvidado un parámetro necesario, una aserción de framework le indicará lo que olvidó.  
  
 Para obtener más información sobre `CCreateContext`, vea el ejemplo MFC [VIEWEX](../../visual-cpp-samples.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)   
 [CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)   
 [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)   
 [CSplitterWnd:: Create](../../mfc/reference/csplitterwnd-class.md#create)   
 [CSplitterWnd:: CreateView](../../mfc/reference/csplitterwnd-class.md#createview)   
 [CWnd:: Create](../../mfc/reference/cwnd-class.md#create)

