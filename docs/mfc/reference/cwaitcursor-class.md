---
title: Clase CWaitCursor | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
dev_langs:
- C++
helpviewer_keywords:
- cursors, wait cursor
- CWaitCursor class
- wait cursors
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: f72598c356add5d891b013f1fd7b87665c5a6c63
ms.lasthandoff: 02/24/2017

---
# <a name="cwaitcursor-class"></a>Clase CWaitCursor
Proporciona una manera de una línea de mostrar un cursor de espera, que se muestra normalmente como un reloj de arena, mientras se está realizando una operación larga.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CWaitCursor  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWaitCursor::CWaitCursor](#cwaitcursor)|Construye un `CWaitCursor` de objeto y se muestra el cursor de espera.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWaitCursor::Restore](#restore)|Restaura el cursor de espera después de que se ha cambiado.|  
  
## <a name="remarks"></a>Comentarios  
 `CWaitCursor`no tiene una clase base.  
  
 Windows buenas prácticas de programación requieren mostrar un cursor de espera siempre que se va a realizar una operación que tarda una cantidad considerable de tiempo.  
  
 Para mostrar un cursor de espera, simplemente defina un `CWaitCursor` variable antes del código que realiza la operación de larga duración. El constructor del objeto hace que el cursor de espera que se mostrará automáticamente.  
  
 Cuando el objeto queda fuera del ámbito (al final del bloque en el que el `CWaitCursor` se declara el objeto), su destructor establece el cursor hasta el cursor anterior. En otras palabras, el objeto realiza automáticamente la limpieza necesaria.  
  
> [!NOTE]
>  Debido a que sus constructores y destructores de funcionan, `CWaitCursor` objetos siempre se declaran como variables locales, nunca se declaran como variables globales ni se asignan con **nueva**.  
  
 Si se realiza una operación que puede provocar el cursor cambiará, como mostrar un cuadro de mensaje o el cuadro de diálogo, la llamada la [restaurar](#restore) función miembro para restaurar el cursor de espera. Es correcto llamar a **restaurar** incluso cuando se muestra actualmente un cursor de espera.  
  
 Otra manera de mostrar un cursor de espera es usar la combinación de [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)y quizás [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). Sin embargo, `CWaitCursor` es más fácil de usar porque no es necesario establecer el cursor hasta el cursor anterior cuando haya terminado con la operación de larga duración.  
  
> [!NOTE]
>  MFC establece o restablece el cursor mediante la [CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor) función virtual. Puede reemplazar esta función para proporcionar un comportamiento personalizado.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CWaitCursor`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
## <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#62;](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]  
  
##  <a name="cwaitcursor"></a>CWaitCursor::CWaitCursor  
 Para mostrar un cursor de espera, sólo es necesario declarar un `CWaitCursor` objeto antes de que el código que realiza la operación de larga duración.  
  
```  
CWaitCursor();
```  
  
### <a name="remarks"></a>Comentarios  
 El constructor hace que el cursor de espera que se mostrará automáticamente.  
  
 Cuando el objeto queda fuera del ámbito (al final del bloque en el que el `CWaitCursor` se declara el objeto), su destructor establece el cursor hasta el cursor anterior. En otras palabras, el objeto realiza automáticamente la limpieza necesaria.  
  
 Puede aprovechar el hecho de que se llama al destructor al final del bloque (que podría ser antes del final de la función) para que el cursor de espera activa sólo una parte de la función. Esta técnica se muestra en el segundo ejemplo siguiente.  
  
> [!NOTE]
>  Debido a que sus constructores y destructores de funcionan, `CWaitCursor` objetos siempre se declaran como variables locales, nunca se declaran como variables globales, ni se asignan con **nueva**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#63;](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]  
  
##  <a name="restore"></a>CWaitCursor::Restore  
 Para restaurar el cursor de espera, llame a esta función después de realizar una operación, como mostrar un cuadro de mensaje o el cuadro de diálogo, que puede cambiar el cursor de espera a otro cursor.  
  
```  
void Restore();
```  
  
### <a name="remarks"></a>Comentarios  
 Está bien para llamar a **restaurar** incluso cuando se muestra actualmente el cursor de espera.  
  
 Si necesita restaurar el cursor de espera mientras se encuentra en una función distinta de aquella en la que el `CWaitCursor` se declara el objeto, se puede llamar a [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#64;](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)   
 [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)   
 [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)   
 [CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)   
 [¿Cómo hago?: cambiar el Cursor del Mouse en una aplicación de clase de Microsoft Foundation](http://go.microsoft.com/fwlink/linkid=128044)




