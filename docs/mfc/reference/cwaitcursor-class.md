---
title: Clase CWaitCursor | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
dev_langs: C++
helpviewer_keywords:
- CWaitCursor [MFC], CWaitCursor
- CWaitCursor [MFC], Restore
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1cf5c850158e445e7695b85e540b1e0c162e621c
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="cwaitcursor-class"></a>Clase CWaitCursor
Proporciona una manera de una línea de mostrar un cursor de espera, que se muestra normalmente como un reloj de arena, mientras se está realizando una operación larga.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CWaitCursor  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWaitCursor::CWaitCursor](#cwaitcursor)|Construye un `CWaitCursor` de objeto y se muestra el cursor de espera.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWaitCursor::Restore](#restore)|Restaura el cursor de espera después de que se ha cambiado.|  
  
## <a name="remarks"></a>Comentarios  
 `CWaitCursor`no tiene una clase base.  
  
 Windows buenas prácticas de programación requieren que mostrar un cursor de espera siempre que se va a realizar una operación que toma una considerable cantidad de tiempo.  
  
 Para mostrar un cursor de espera, solo para definir un `CWaitCursor` variable antes que el código que realiza la operación de larga duración. El constructor del objeto hace que el cursor de espera que se mostrará automáticamente.  
  
 Cuando el objeto queda fuera del ámbito (al final del bloque en el que el `CWaitCursor` se declara un objeto), su destructor establece el cursor hasta el cursor anterior. En otras palabras, el objeto realiza la limpieza necesaria automáticamente.  
  
> [!NOTE]
>  Debido a cómo funcionan las sus constructores y destructores, `CWaitCursor` objetos siempre se declaran como variables locales, nunca se han declarado como variables globales ni se asignan con **nueva**.  
  
 Si lleva a cabo una operación que podría producir el cursor cambiarse, como mostrar un cuadro de mensaje o el cuadro de diálogo, la llamada la [restaurar](#restore) función de miembro para restaurar el cursor de espera. Es correcto llamar a **restaurar** incluso cuando se muestra actualmente un cursor de espera.  
  
 Otra manera de mostrar un cursor de espera es usar la combinación de [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)y quizás [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). Sin embargo, `CWaitCursor` es más fácil de usar porque no es necesario establecer el cursor hasta el cursor anterior cuando haya terminado con la operación de larga duración.  
  
> [!NOTE]
>  MFC establece o restablece el cursor mediante la [CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor) función virtual. Puede invalidar esta función para proporcionar un comportamiento personalizado.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CWaitCursor`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
## <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]  
  
##  <a name="cwaitcursor"></a>CWaitCursor::CWaitCursor  
 Para mostrar un cursor de espera, solo tiene que declarar un `CWaitCursor` objeto antes de que el código que realiza la operación de larga duración.  
  
```  
CWaitCursor();
```  
  
### <a name="remarks"></a>Comentarios  
 El constructor hace que el cursor de espera que se mostrará automáticamente.  
  
 Cuando el objeto queda fuera del ámbito (al final del bloque en el que el `CWaitCursor` se declara un objeto), su destructor establece el cursor hasta el cursor anterior. En otras palabras, el objeto realiza la limpieza necesaria automáticamente.  
  
 Puede aprovechar el hecho de que se llama al destructor al final del bloque (que podría ser anterior al final de la función) para activar el cursor de espera en solo una parte de la función. Esta técnica se muestra en el segundo ejemplo siguiente.  
  
> [!NOTE]
>  Debido a cómo funcionan las sus constructores y destructores, `CWaitCursor` objetos siempre se declaran como variables locales, nunca se han declarado como variables globales, ni se asignan con **nueva**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]  
  
##  <a name="restore"></a>CWaitCursor::Restore  
 Para restaurar el cursor de espera, llame a esta función después de realizar una operación, como mostrar un cuadro de mensaje o el cuadro de diálogo que puede cambiar el cursor de espera a otro cursor.  
  
```  
void Restore();
```  
  
### <a name="remarks"></a>Comentarios  
 Puede llamar a **restaurar** incluso cuando se muestra actualmente el cursor de espera.  
  
 Si tiene que restaurar el cursor de espera mientras se encuentra en una función distinta de aquella en la que el `CWaitCursor` se declara el objeto, puede llamar a [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)   
 [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)   
 [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)   
 [CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)   
 [¿Cómo I: cambia el Cursor del Mouse en una aplicación de clase de Microsoft Foundation](http://go.microsoft.com/fwlink/p/?linkid=128044)



