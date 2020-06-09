---
title: Archivo (Menú en una aplicación de base de datos MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- File menu
- database applications [MFC], File menu commands
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
ms.openlocfilehash: fbbb4382749278708e8e758f79a618d5cad0549e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615699"
---
# <a name="file-menu-in-an-mfc-database-application"></a>Archivo (Menú en una aplicación de base de datos MFC)

Si crea una aplicación de base de datos MFC y no utiliza la serialización, ¿cómo debe interpretar los comandos abrir, cerrar, guardar y guardar como en el menú Archivo, pero no hay ninguna guía de estilo para esta pregunta, estas son algunas sugerencias:

- Elimine completamente el comando abrir del menú archivo.

- Interprete el comando Open como "Open Database" y muestre al usuario una lista de orígenes de datos que la aplicación reconoce.

- Interprete el comando Abrir como, quizás, "abrir perfil". Mantenga abierto para abrir un archivo serializado, pero use el archivo para almacenar un documento serializado que contenga información de "Perfil de usuario", como las preferencias del usuario, incluido su identificador de inicio de sesión (opcionalmente excluyendo la contraseña) y el origen de datos con el que trabajó más recientemente.

El Asistente para aplicaciones MFC admite la creación de una aplicación sin ningún comando de menú archivo relacionado con el documento. Seleccione la opción **vista de base de datos sin soporte de archivo** en la página **compatibilidad con bases de datos** .

Para interpretar un comando de menú Archivo de una manera especial, debe invalidar uno o más controladores de comandos, principalmente en la `CWinApp` clase derivada de. Por ejemplo, si invalida completamente `OnFileOpen` (que implementa el `ID_FILE_OPEN` comando) para indicar "base de datos abierta:"

- No llame a la versión de la clase base de `OnFileOpen` , ya que está reemplazando por completo la implementación predeterminada del marco del comando.

- En su lugar, utilice el controlador para mostrar un cuadro de diálogo que muestre los orígenes de datos. Para mostrar este cuadro de diálogo, puede llamar a `CDatabase::OpenEx` o `CDatabase::Open` con el parámetro **null**. Se abrirá un cuadro de diálogo ODBC que muestra todos los orígenes de datos disponibles en el equipo del usuario.

- Dado que las aplicaciones de base de datos no suelen guardar todo un documento, es probable que quiera quitar las implementaciones guardar y guardar como, a menos que use un documento serializado para almacenar información de perfil. De lo contrario, podría implementar el comando Guardar como, por ejemplo, "COMMIT TRANSACTION". Vea la [Nota técnica 22](tn022-standard-commands-implementation.md) para obtener más información sobre la invalidación de estos comandos.

## <a name="see-also"></a>Consulte también

[Serialización: Serialización frente a entrada/salida de bases de datos](serialization-serialization-vs-database-input-output.md)
