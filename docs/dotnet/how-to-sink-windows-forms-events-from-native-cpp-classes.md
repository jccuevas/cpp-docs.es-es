---
title: Filtrar Receptor de eventos de Windows Forms de clases nativas de C++
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, managed/native interop
- event handling, sinking .NET in C++
- event handling, .NET/native interop
- event handling, Windows Forms in C++
ms.assetid: 6e30ddee-d058-4c8d-9956-2a43d86f19d5
ms.openlocfilehash: d02bcea4efce03c8fb11650d344468236737cfbd
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738778"
---
# <a name="how-to-sink-windows-forms-events-from-native-c-classes"></a>Filtrar Receptor de eventos de Windows Forms de clases nativas de C++

Puede habilitar clases de C++ nativas recibir devoluciones de llamada desde eventos administrados generados desde los controles de formularios Windows Forms u otros formularios con el formato de mapa de macros de MFC. Recibir eventos en las vistas y cuadros de diálogo es similar a la misma tarea para los controles.

Para ello, deberá:

- Adjuntar un `OnClick` controlador de eventos para el control mediante [MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate).

- Crear un mapa de delegado mediante [BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map), [END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map), y [EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry).

Este ejemplo continúa el trabajo realizado en [Cómo: Realizar enlaces de datos DDX/DDV con formularios Windows](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

Ahora, se asociará el control MFC (`m_MyControl`) con un delegado de controlador de eventos administrado llamado `OnClick` para los recursos administrados <xref:System.Windows.Forms.Control.Click> eventos.

### <a name="to-attach-the-onclick-event-handler"></a>Para asociar el controlador de eventos OnClick:

1. Agregue el código siguiente a la implementación de BOOL CMFC01Dlg:: OnInitDialog:

    ```
    m_MyControl.GetControl()->button1->Click += MAKE_DELEGATE( System::EventHandler, OnClick );
    ```

1. Agregue el código siguiente a la sección pública de la declaración de clase CMFC01Dlg: CDialog público.

    ```
    // delegate map
    BEGIN_DELEGATE_MAP( CMFC01Dlg )
    EVENT_DELEGATE_ENTRY( OnClick, System::Object^, System::EventArgs^ )
    END_DELEGATE_MAP()

    void OnClick( System::Object^ sender, System::EventArgs^ e );
    ```

1. Por último, agregue la implementación de `OnClick` a CMFC01Dlg.cpp:

    ```
    void CMFC01Dlg::OnClick(System::Object^ sender, System::EventArgs^ e)
    {
        AfxMessageBox(_T("Button clicked"));
    }
    ```

## <a name="see-also"></a>Vea también

[MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate)<br/>
[BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map)<br/>
[END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map)<br/>
[EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry)
