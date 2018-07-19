---
title: Agregar controles a un cuadro de diálogo, el cuadro de diálogo ya No funcionar | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], troubleshooting
- common controls, troubleshooting
- troubleshooting controls
- dialog boxes, troubleshooting
- dialog box controls, troubleshooting
- InitCommonControls
ms.assetid: b2dd4574-ea59-4343-8d65-b387cead5da6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b10c24955e74d08ab570b5b694628f42bb394268
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858999"
---
# <a name="adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function"></a>Al agregar controles a un cuadro de diálogo, éste deja de funcionar
Después de agregar un control común o un control rich edit a un cuadro de diálogo, no aparecerá cuando se prueba el cuadro de diálogo o el cuadro de diálogo no aparecerá.  
  
 **Ejemplo del problema**  
  
1.  Cree un proyecto Win32, modifique la configuración de la aplicación para crear una aplicación de Windows (no una aplicación de consola).  
  
2.  En [vista de recursos](../windows/resource-view-window.md), haga doble clic en el archivo .rc.  
  
3.  En la opción de cuadro de diálogo, haga doble clic en el **sobre** cuadro.  
  
4.  Agregar un **Control de dirección IP** al cuadro de diálogo.  
  
5.  Guardar y **volver a generar todo**.  
  
6.  Ejecute el programa.  
  
7.  En el cuadro de diálogo **ayuda** menú, haga clic en el **sobre** comando; ningún cuadro de diálogo se muestra el cuadro.  
  
 **La causa**  
  
 Actualmente, el editor de cuadro de diálogo no agrega automáticamente código a su proyecto cuando arrastra y coloca los siguientes controles comunes o controles rich edit en un cuadro de diálogo. Ni Visual Studio ofrece un error o una advertencia cuando se produce este problema. Debe agregar manualmente el código para el control.  
  
||||  
|-|-|-|  
|Control deslizante|Control de árbol|Date Time Picker|  
|Control de número|Control de pestaña|Calendario mensual|  
|Control de progreso|Control de animación|IP Address Control|  
|Tecla de acceso rápido|Control Rich Edit|Cuadro combinado extendido|  
|Control de lista|Control Rich Edit 2.0|Control personalizado|  
  
## <a name="the-fix-for-common-controls"></a>La corrección para los controles comunes  
 Para poder utilizar controles comunes en un cuadro de diálogo, debe llamar a [InitCommonControlsEx](http://msdn.microsoft.com/library/windows/desktop/bb775697) o **AFXInitCommonControls** antes de crear el cuadro de diálogo.  
  
## <a name="the-fix-for-richedit-controls"></a>La corrección para controles RichEdit  
 Debe llamar a **LoadLibrary** para controles rich edit. Para obtener más información, consulte [con el Control RichEdit 1.0 con MFC](../windows/using-the-richedit-1-0-control-with-mfc.md), [acerca de los controles Rich Edit](http://msdn.microsoft.com/library/windows/desktop/bb787873) en el [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)], y [información general sobre el Control Rich Edit](../mfc/overview-of-the-rich-edit-control.md).  
  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Solucionar problemas del Editor de cuadro de diálogo](../windows/troubleshooting-the-dialog-editor.md)   
 [Editor de cuadros de diálogo](../windows/dialog-editor.md)

