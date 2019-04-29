---
title: Archivos DLL MFC estándar vinculadas dinámicamente a MFC
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- AFX_MANAGE_STATE macro
- DLLs [C++], regular
- shared DLL versions [C++]
- dynamically linked DLLs [C++]
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
ms.openlocfilehash: 3bfed5f75dab4c501708950fdb99f53c40ec142c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315006"
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>Archivos DLL MFC estándar vinculadas dinámicamente a MFC

Normal que MFC DLL vinculado dinámicamente a MFC es un archivo DLL utiliza MFC internamente y las funciones exportadas en el archivo DLL se pueden llamar desde archivos ejecutables MFC o no MFC. Como se describe en el nombre, este tipo de archivo DLL se compila con la versión de la biblioteca de vínculos dinámicos de MFC (también conocida como la versión compartida de MFC). Las funciones se suelen exportar desde DLL de MFC mediante la interfaz estándar de C normal.

Debe agregar el `AFX_MANAGE_STATE` macro al principio de todas las funciones exportadas en archivos DLL de MFC estándar vinculados dinámicamente a MFC para establecer el estado actual del módulo en el otro para el archivo DLL. Esto se realiza mediante la adición de la línea de código siguiente al principio de las funciones exportadas desde el archivo DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

Vinculados dinámicamente a MFC normal DLL de MFC, tiene las siguientes características:

- Se trata de un nuevo tipo de DLL introducido por Visual C++ 4.0.

- El archivo ejecutable del cliente puede escribirse en cualquier lenguaje que admite el uso de archivos DLL (C, C++, Pascal, Visual Basic y así sucesivamente); no tiene que ser una aplicación MFC.

- A diferencia de la DLL de MFC estándar vinculado estáticamente, este tipo de archivo DLL se vincula dinámicamente a la DLL de MFC (también conocida como la DLL de MFC compartido).

- La biblioteca de importación MFC vinculada a este tipo de archivo DLL es el mismo que se usa para archivos DLL de extensión MFC o las aplicaciones que usan la DLL de MFC: MFCxx(D).lib.

Vinculados dinámicamente a MFC normal DLL de MFC, tiene los siguientes requisitos:

- Estos archivos DLL se compilan con **_AFXDLL** definido, como un archivo ejecutable que se vincule dinámicamente a la DLL de MFC. Pero **_USRDLL** también se define como una DLL de MFC normal que se vincula estáticamente a MFC.

- Debe crear una instancia de este tipo de DLL un `CWinApp`-clase derivada.

- Este tipo de archivo DLL utiliza la `DllMain` proporcionadas por MFC. Colocar todo código de inicialización específica para DLL el `InitInstance` código de función y de finalización de miembros en `ExitInstance` como en una aplicación MFC normal.

Dado que este tipo de archivo DLL utiliza la versión de la biblioteca de vínculos dinámicos de MFC, debe establecer explícitamente el estado actual del módulo a del archivo DLL. Para ello, use el [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) macro al principio de cada función exportada desde el archivo DLL.

Archivos DLL de MFC estándar debe tener un `CWinApp`-derivados de clase y un único objeto de esa clase de aplicación, como una aplicación MFC. Sin embargo, el `CWinApp` objeto del archivo DLL no tiene un suministro de mensajes principal, como hace el `CWinApp` objeto de una aplicación.

Tenga en cuenta que el `CWinApp::Run` mecanismo no se aplica a un archivo DLL, porque la aplicación es propietaria del suministro de mensajes principal. Si el archivo DLL muestra cuadros de diálogo no modales o tiene una ventana de marco principal de su propio, el bombeo de mensajes principal de la aplicación debe llamar a una rutina exportada por el archivo DLL que llama a `CWinApp::PreTranslateMessage`.

Colocar toda la inicialización específica para DLL en el `CWinApp::InitInstance` función miembro como en una aplicación MFC normal. El `CWinApp::ExitInstance` función miembro de su `CWinApp` se llama a una clase derivada de MFC proporcionado `DllMain` funcionar antes de que se descarga el archivo DLL.

Debe distribuir los archivos DLL compartidos MFCx0.dll y Msvcr*0.dll (o archivos similares) con la aplicación.

Un archivo DLL que se vincule dinámicamente a MFC no se puede vincular también estáticamente a MFC. Vínculo de aplicaciones a los archivos DLL de MFC estándar vinculados dinámicamente a MFC, al igual que cualquier otro archivo DLL.

Símbolos normalmente se exportan desde la DLL de MFC mediante la interfaz estándar de C normal. La declaración de una función exportada desde un archivo DLL MFC tiene un aspecto similar al siguiente:

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Todas las asignaciones de memoria dentro de un archivo DLL MFC deben permanecer dentro de la DLL; el archivo DLL no debe pasar a o recibir desde el archivo ejecutable de llamada cualquiera de las siguientes acciones:

- Punteros a objetos MFC

- Punteros a la memoria asignada por MFC

Si necesita realizar cualquiera de los pasos anteriores, o si tiene que pasar objetos derivados de MFC entre el archivo ejecutable de llamada y el archivo DLL, deberá generar un archivo DLL de extensión MFC.

Es seguro pasar punteros a la memoria asignados por las bibliotecas de tiempo de ejecución de C entre una aplicación y un archivo DLL solo si realiza una copia de los datos. No debe eliminar o cambiar el tamaño de estos punteros o usarlos sin tener que realizar una copia de la memoria.

Al compilar un archivo DLL MFC que dinámicamente se vincule a MFC, deberá utilizar la macro [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) para cambiar el estado del módulo MFC correctamente. Esto se realiza mediante la adición de la línea de código siguiente al principio de las funciones exportadas desde el archivo DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

El **AFX_MANAGE_STATE** macro no debe usarse en archivos DLL de MFC estándar vinculados estáticamente a MFC o en archivos DLL de extensión MFC. Para obtener más información, consulte [administrar los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md).

Para obtener un ejemplo de cómo escribir, crear y usar un archivo DLL MFC, vea el ejemplo [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap). Para obtener más información sobre archivos DLL de MFC estándar vinculados dinámicamente a MFC, vea la sección titulada "Convertir DLLScreenCap a dinámicamente vínculo DLL de MFC" en el resumen del ejemplo.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Inicializar archivos DLL de MFC estándar](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Estados de módulos de una DLL de MFC estándar vinculados dinámicamente a MFC](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)

- [Administrar los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

- [Uso de archivos DLL de extensión MFC de base de datos, OLE y Sockets en archivos DLL de MFC estándar](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Usar MFC como parte de un archivo DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

## <a name="see-also"></a>Vea también

[Tipos de archivos DLL](kinds-of-dlls.md)
