---
title: Compatibilidad MAPI en MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, MAPI support
- MAPI support in MFC
- CDocument class [MFC], and MAPI
- OnUpdateFileSendMail method [MFC]
- MAPI, MFC
- OnFileSendMail method [MFC]
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
ms.openlocfilehash: 7eff22b2a7b4c838f2967fb5217b9dec96903d0e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625570"
---
# <a name="mapi-support-in-mfc"></a>Compatibilidad MAPI en MFC

MFC proporciona compatibilidad con un subconjunto de la interfaz de programación de aplicaciones de mensajería (MAPI) de Microsoft en la clase `CDocument` . En concreto, `CDocument` tiene funciones miembro que determinan si la compatibilidad con correo está presente en el equipo del usuario final y, si es así, habilitan un comando enviar correo cuyo identificador de comando estándar es ID_FILE_SEND_MAIL. La función de controlador de MFC para este comando permite al usuario enviar un documento por correo electrónico.

> [!TIP]
> Aunque MFC no encapsula el conjunto completo de funciones MAPI, todavía se pueden llamar directamente a las funciones MAPI, de la misma forma que se puede llamar a funciones de la API Win32 directamente desde programas MFC.

Proporcionar el comando enviar correo en la aplicación es muy fácil. MFC proporciona la implementación para empaquetar un documento (es decir, un `CDocument` objeto derivado de) como datos adjuntos y enviarlo como correo. Estos datos adjuntos son equivalentes a un comando Guardar archivo que guarda (serializa) el contenido del documento en el mensaje de correo. Esta implementación llama al cliente de correo en el equipo del usuario para proporcionar al usuario la oportunidad de direccionar el correo y agregar el asunto y el texto del mensaje al mensaje de correo. Los usuarios ven la interfaz de usuario de la aplicación de correo que ya conoce. Esta funcionalidad la proporcionan dos `CDocument` funciones miembro: `OnFileSendMail` y `OnUpdateFileSendMail` .

MAPI debe leer el archivo para enviar los datos adjuntos. Si la aplicación mantiene su archivo de datos abierto durante una `OnFileSendMail` llamada de función, el archivo debe abrirse con un modo de uso compartido que permita que varios procesos tengan acceso al archivo.

> [!NOTE]
> Una versión de reemplazo de `OnFileSendMail` para la clase `COleDocument` controla correctamente los documentos compuestos.

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>Para implementar un comando enviar correo con MFC

1. Use el editor de menús de Visual C++ para agregar un elemento de menú cuyo identificador de comando sea ID_FILE_SEND_MAIL.

   El marco de trabajo proporciona este identificador de comando en AFXRES. C. El comando se puede Agregar a cualquier menú, pero normalmente se agrega al menú **archivo** .

1. Agregue manualmente lo siguiente al mapa de mensajes del documento:

   [!code-cpp[NVC_MFCDocView#9](codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  Este mapa de mensajes funciona para un documento derivado de `CDocument` o `COleDocument` : selecciona la clase base correcta en cualquier caso, aunque el mapa de mensajes se encuentra en la clase de documento derivada.

1. Compile la aplicación.

Si la compatibilidad con correo está disponible, MFC habilita el elemento de menú con `OnUpdateFileSendMail` y, posteriormente, procesa el comando con `OnFileSendMail` . Si no está disponible la compatibilidad con correo, MFC quita automáticamente el elemento de menú para que el usuario no lo vea.

> [!TIP]
> En lugar de agregar manualmente las entradas de mapa de mensajes tal y como se ha descrito anteriormente, puede usar el [Asistente para clases](reference/mfc-class-wizard.md) de clase para asignar mensajes a funciones. Para obtener más información, vea [asignar mensajes a funciones](reference/mapping-messages-to-functions.md).

Para obtener información relacionada, consulte la introducción a [MAPI](mapi.md) .

Para obtener más información acerca de las `CDocument` funciones miembro que habilitan MAPI, consulte:

- [CDocument:: OnFileSendMail](reference/cdocument-class.md#onfilesendmail)

- [CDocument:: OnUpdateFileSendMail](reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument:: OnFileSendMail](reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>Consulte también

[MAPI](mapi.md)
