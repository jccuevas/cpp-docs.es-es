---
title: 'Cómo: Agregar compatibilidad con el Administrador de reinicio'
ms.date: 11/04/2016
helpviewer_keywords:
- Restart manager [MFC]
- C++, application crash support
ms.assetid: 7f3f5867-d4bc-4ba8-b3c9-dc1e7be93642
ms.openlocfilehash: 848cb3bb52ae13eb1b7798126becd13384fddeb6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625654"
---
# <a name="how-to-add-restart-manager-support"></a>Cómo: Agregar compatibilidad con el Administrador de reinicio

El administrador de reinicio es una característica agregada a Visual Studio para Windows Vista o sistemas operativos posteriores. El Administrador de reinicio agrega compatibilidad para la aplicación en caso de cierre o reinicio de forma inesperada. El comportamiento del Administrador de reinicio depende del tipo de aplicación. Si la aplicación es un editor de documentos, el Administrador de reinicio permite que la aplicación guarde automáticamente el estado y el contenido de cualquier documento abierto y reinicia la aplicación después de que se cierre de forma inesperada. Si la aplicación no es un editor de documentos, el Administrador de reinicio reinicia la aplicación, pero no puede guardar el estado de la aplicación de forma predeterminada.

Después del reinicio, la aplicación muestra un cuadro de diálogo de tarea si la aplicación es Unicode. Si se trata de una aplicación ANSI, muestra un cuadro de mensaje de Windows. En este punto, el usuario decide si se deben restaurar los documentos guardados automáticamente. Si el usuario no restaura los documentos guardados automáticamente, el Administrador de reinicio descarta los archivos temporales.

> [!NOTE]
> Puede reemplazar el comportamiento predeterminado del Administrador de reinicio para guardar los datos y reiniciar la aplicación.

De forma predeterminada, las aplicaciones MFC creadas con el Asistente para proyectos de Visual Studio admiten el administrador de reinicio cuando las aplicaciones se ejecutan en un equipo que tiene un sistema operativo Windows Vista o posterior. Si no desea que la aplicación admita el Administrador de reinicio, puede deshabilitarlo en el asistente para nuevo proyecto.

### <a name="to-add-support-for-the-restart-manager-to-an-existing-application"></a>Para agregar compatibilidad con el Administrador de reinicio a una aplicación existente

1. Abra una aplicación MFC existente en Visual Studio.

1. Abra el archivo de código fuente de la aplicación principal. De forma predeterminada, es el archivo .cpp que tiene el mismo nombre que la aplicación. Por ejemplo, el archivo de código fuente de la aplicación principal para MyProject es MyProject.cpp.

1. Busque el constructor de la aplicación principal. Por ejemplo, si el proyecto es MyProject, el constructor es `CMyProjectApp::CMyProjectApp()`.

1. Agregue la siguiente línea de código al constructor:

```
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;
```

1. Asegúrese de que el método `InitInstance` de la aplicación llama a su método principal `InitInstance` : [CWinApp::InitInstance](reference/cwinapp-class.md#initinstance) o `CWinAppEx::InitInstance`. El `InitInstance` método es responsable de comprobar el parámetro *m_dwRestartManagerSupportFlags* .

1. Compile y ejecute la aplicación.

## <a name="see-also"></a>Consulte también

[CDataRecoveryHandler (clase)](reference/cdatarecoveryhandler-class.md)<br/>
[CWinApp:: m_dwRestartManagerSupportFlags](reference/cwinapp-class.md#m_dwrestartmanagersupportflags)<br/>
[CWinApp (clase)](reference/cwinapp-class.md)<br/>
[CWinApp:: m_nAutosaveInterval](reference/cwinapp-class.md#m_nautosaveinterval)<br/>
[CDocument:: OnDocumentEvent](reference/cdocument-class.md#ondocumentevent)
