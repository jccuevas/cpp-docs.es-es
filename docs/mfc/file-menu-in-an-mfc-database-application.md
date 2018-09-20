---
title: Menú archivo en una aplicación de base de datos MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- File menu
- database applications [MFC], File menu commands
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5fe90e01ec53711f47418d4512262e2e05e62f26
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425137"
---
# <a name="file-menu-in-an-mfc-database-application"></a>Archivo (Menú en una aplicación de base de datos MFC)

Si crea una aplicación de base de datos MFC y no utiliza la serialización, cómo debe interpretar la apertura, cierre, guardar y guardar como comandos en el menú archivo aunque no hay ninguna directriz de estilo para esta pregunta, estas son algunas sugerencias:

- Eliminar completamente el comando Abrir del menú archivo.

- Interprete el comando Abrir como "Abrir base de datos" y mostrar al usuario una lista de orígenes de datos de que la aplicación reconozca.

- Interprete el comando Abrir como, quizás, "abrir perfil". Conserve abierto para abrir un archivo serializado, pero se use el archivo para almacenar un documento serializado que contiene información de "perfil de usuario", como las preferencias del usuario, incluida su o su Id. de inicio de sesión (excluyendo opcionalmente la contraseña) y el origen de datos que más recientemente se ha trabajado con.

El Asistente para aplicaciones MFC admite la creación de una aplicación con ningún comandos del menú archivo relacionados con el documento. Seleccione el **vista sin compatibilidad con archivos de base de datos** opción el **base de datos admite** página.

Para interpretar un comando de menú archivo de una manera especial, debe reemplazar uno o varios controladores de comandos, principalmente en su `CWinApp`-clase derivada. Por ejemplo, si reemplaza completamente `OnFileOpen` (que implementa el `ID_FILE_OPEN` comando) significa "Abrir base de datos:"

- No llame a la versión de la clase base `OnFileOpen`, ya que se va a reemplazar completamente implementación de predeterminada de .NET framework del comando.

- Utilice en su lugar, el controlador para mostrar un cuadro de diálogo lista de orígenes de datos. Puede mostrar un cuadro de diálogo tal mediante una llamada a `CDatabase::OpenEx` o `CDatabase::Open` con el parámetro **NULL**. Se abrirá un cuadro de diálogo ODBC que muestra todos los orígenes de datos disponibles en el equipo del usuario.

- Dado que las aplicaciones de base de datos normalmente no guardan un documento completo, probablemente deseará quitar al guardar y guardar como implementaciones a menos que utilice un documento serializado para almacenar información de perfil. En caso contrario, podría implementar el comando Guardar como, por ejemplo, "Confirmar transacción". Consulte [Nota técnica 22](../mfc/tn022-standard-commands-implementation.md) para obtener más información sobre cómo reemplazar estos comandos.

## <a name="see-also"></a>Vea también

[Serialización: Serialización frente a Base de datos de entrada/salida](../mfc/serialization-serialization-vs-database-input-output.md)

