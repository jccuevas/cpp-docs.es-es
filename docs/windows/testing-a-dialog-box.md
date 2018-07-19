---
title: Probar un cuadro de diálogo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Test Dialog command
- testing, dialog boxes
- dialog boxes, testing
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 57bb9e827caae0e328971077d902673f2428c80b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889551"
---
# <a name="testing-a-dialog-box"></a>Probar un cuadro de diálogo
Cuando se está diseñando un cuadro de diálogo, se puede simular y probar su comportamiento en tiempo de ejecución sin compilar el programa. En este modo, se puede:  
  
-   Escribir texto, seleccionar opciones de listas de cuadro combinado, activar y desactivar opciones y elegir comandos.  
  
-   Probar el orden de tabulación.  
  
-   Probar la agrupación de controles, como botones de radio y casillas.  
  
-   Probar los métodos abreviados de teclado para los controles del cuadro de diálogo.  
  
    > [!NOTE]
    >  Las conexiones con el código del cuadro de diálogo realizadas mediante asistentes no se incluyen en la simulación.  
  
 Cuando se prueba un cuadro de diálogo, normalmente se muestra en una ubicación relativa a la ventana principal del programa. Si la propiedad Absolute Align del cuadro de diálogo se establece en True, este se muestra en una posición relativa a la esquina superior izquierda de la pantalla.  
  
### <a name="to-test-a-dialog-box"></a>Para probar un cuadro de diálogo  
  
1.  Cuando el Editor de cuadros de diálogo es la ventana activa, en la barra de menús, elija **Formato**, **Probar cuadro de diálogo**.  
  
2.  Para finalizar la simulación, presione ESC o elija simplemente el botón **Cerrar** del cuadro de diálogo que está probando.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index).  
  
 Requisitos  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)   
 [Editor de cuadro de diálogo](../windows/dialog-editor.md)   
 [Mostrar u ocultar la barra de herramientas del Editor de cuadros de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)

