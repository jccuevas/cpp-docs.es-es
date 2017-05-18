---
title: Estructura de CCreateContext | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCreateContext
dev_langs:
- C++
helpviewer_keywords:
- CCreateContext structure
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
caps.latest.revision: 22
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 231f2e44e085d27a2b2cbf289adf7b0521471b0e
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="ccreatecontext-structure"></a>Estructura de CCreateContext
El marco de trabajo usa el `CCreateContext` estructura cuando crea las ventanas de marco y vistas que están asociadas a un documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct CCreateContext  
```  
  
## <a name="remarks"></a>Comentarios  
 `CCreateContext`es una estructura y no tiene una clase base.  
  
 Cuando se crea una ventana, los valores de esta estructura proporcionan la información utilizada para conectar los componentes de un documento a la vista de sus datos. Sólo tiene que usar `CCreateContext` si va a reemplazar partes del proceso de creación.  
  
 Un `CCreateContext` estructura contiene punteros a la plantilla de documento, la ventana de marco, la vista y el documento. También contiene un puntero a un `CRuntimeClass` que identifica el tipo de vista para crear. La información de clase en tiempo de ejecución y el puntero del documento actual se utilizan para crear una nueva vista de forma dinámica. La siguiente tabla sugiere cómo y cuándo cada `CCreateContext` podría utilizarse el miembro:  
  
|Miembro|Tipo|¿Qué es|  
|------------|----------|--------------------|  
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass`de la nueva vista que se va a crear.|  
|`m_pCurrentDoc`|`CDocument*`|El documento existente que se asociará con la nueva vista.|  
|`m_pNewDocTemplate`|`CDocTemplate*`|La plantilla de documento asociada a la creación de una nueva ventana de marco MDI.|  
|`m_pLastView`|`CView*`|La vista original en el que se modelan vistas adicionales, como se muestra en la creación de vistas de la ventana divisora o la creación de una segunda vista en un documento.|  
|`m_pCurrentFrame`|`CFrameWnd*`|La ventana de marco en el que se modelan ventanas de marco adicionales, como se muestra en la creación de una segunda ventana de marco en un documento.|  
  
 Cuando una plantilla de documento crea un documento y sus componentes asociados, valida la información almacenada en el `CCreateContext` estructura. Por ejemplo, no se debe crear una vista para un documento que no existe.  
  
> [!NOTE]
>  Todos los punteros de `CCreateContext` son opcionales y pueden ser `NULL` si desconocido o no especificado.  
  
 `CCreateContext`usa las funciones de miembro aparecen bajo "Vea también". Si planea reemplazar, consulte las descripciones de estas funciones para obtener información específica.  
  
 Estas son algunas directrices generales:  
  
-   Cuando se pasa como un argumento para la creación de la ventana, como en `CWnd::Create`, `CFrameWnd::Create`, y `CFrameWnd::LoadFrame`, el contexto de creación especifica qué opciones que se debe conectar a la nueva ventana. Para la mayoría de las ventanas, la estructura completa es opcional y un `NULL` se puede pasar el puntero.  
  
-   Para las funciones miembro reemplazables, como `CFrameWnd::OnCreateClient`, el `CCreateContext` argumento es opcional.  
  
-   Para las funciones miembro implicadas en la vista creación, debe proporcionar información suficiente para crear la vista. Por ejemplo, para la primera vista en una ventana divisora, debe proporcionar la información de la clase de vista y el documento actual.  
  
 En general, si utiliza los valores predeterminados de framework, puede omitir `CCreateContext`. Si intenta modificaciones más avanzadas, el código fuente de Microsoft Foundation Class Library o los programas de ejemplo, como VIEWEX, le ayudará. Si olvida un parámetro necesario, una aserción de framework le indicará lo que ha olvidado.  
  
 Para obtener más información sobre `CCreateContext`, vea el ejemplo MFC [VIEWEX](../../visual-cpp-samples.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)   
 [CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)   
 [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)   
 [CSplitterWnd:: Create](../../mfc/reference/csplitterwnd-class.md#create)   
 [CSplitterWnd:: CreateView](../../mfc/reference/csplitterwnd-class.md#createview)   
 [CWnd:: Create](../../mfc/reference/cwnd-class.md#create)


