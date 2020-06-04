---
title: Archivos DLL de MFC estándar vinculados dinámicamente a MFC
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315006"
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>Archivos DLL de MFC estándar vinculados dinámicamente a MFC

Un archivo DLL de MFC estándar vinculado dinámicamente a MFC es una DLL que usa MFC de forma interna, y las funciones exportadas en el archivo DLL se pueden llamar mediante archivos ejecutables de MFC o no basados en MFC. Como su nombre indica, este tipo de archivos DLL se compilan con la versión de biblioteca de vínculos dinámicos de MFC (conocida también como la versión compartida de MFC). Las funciones se suelen exportar desde un archivo DLL de MFC estándar mediante la interfaz estándar de C.

Debe agregar la macro `AFX_MANAGE_STATE` al principio de todas las funciones exportadas en archivos DLL de MFC estándar que se vinculan dinámicamente a MFC para establecer el estado actual del módulo en el del archivo DLL. Para hacerlo, agregue la línea de código siguiente al principio de las funciones exportadas desde el archivo DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

Un archivo DLL de MFC estándar vinculado dinámicamente a MFC tiene las características siguientes:

- Se trata de un nuevo tipo de DLL que se ha introducido en Visual C++ 4.0.

- El ejecutable del cliente se puede escribir en cualquier lenguaje que admita el uso de archivos DLL (C, C++, Pascal, Visual Basic, etc.); no tiene que ser una aplicación MFC.

- A diferencia del archivo DLL de MFC estándar vinculado estáticamente, este tipo de DLL se vincula dinámicamente al de MFC (conocido también como archivo DLL compartido de MFC).

- La biblioteca de importación de MFC vinculada a este tipo de DLL es la misma que se usa para los archivos DLL de extensión de MFC o para las aplicaciones que usan el DLL de MFC: MFCxx(D).lib.

Un archivo DLL de MFC estándar vinculado dinámicamente a MFC tiene los requisitos siguientes:

- Estos archivos DLL se compilan con **_AFXDLL** definido, igual que los archivos ejecutables vinculados dinámicamente al archivo DLL de MFC. Aun así, también se define **_USRDLL**, igual que sucede en los archivos DLL de MFC estándar vinculados estáticamente a MFC.

- Este tipo de DLL debe crear una instancia de una clase derivada de `CWinApp`.

- Este tipo de DLL usa el elemento `DllMain` proporcionado por MFC. Coloque todo el código de inicialización específico del archivo DLL en la función miembro `InitInstance` y el código de finalización en `ExitInstance`, como en una aplicación MFC estándar.

Dado que este tipo de archivo DLL usa la versión de biblioteca de vínculos dinámicos de MFC, debe establecer explícitamente el estado actual del módulo en el del archivo DLL. Para ello, use la macro [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) al principio de todas las funciones exportadas desde el archivo DLL.

Los archivos DLL de MFC estándar deben tener una clase derivada de `CWinApp` y un solo objeto de esa clase de aplicación, igual que una aplicación MFC. Pero el objeto `CWinApp` del archivo DLL no tiene un suministro de mensajes principal, a diferencia del objeto `CWinApp` de una aplicación.

Tenga en cuenta que el mecanismo `CWinApp::Run` no se aplica a un archivo DLL, porque la aplicación es la propietaria del suministro de mensajes principal. Si el archivo DLL muestra cuadros de diálogo sin modo o tiene una ventana de marco principal propia, el suministro de mensajes principal de la aplicación deberá llamar a una rutina exportada por el archivo DLL que llame a `CWinApp::PreTranslateMessage`.

Coloque todo el código de inicialización específico del archivo DLL en la función miembro `CWinApp::InitInstance`, como en una aplicación MFC estándar. Se llama a la función miembro `CWinApp::ExitInstance` de la clase derivada de `CWinApp` desde la función `DllMain` proporcionada por MFC antes de que se descargue el archivo DLL.

Debe distribuir los archivos DLL compartidos MFCx0.dll y Msvcr*0.dll (o archivos similares) con la aplicación.

Un archivo DLL que se vincula dinámicamente a MFC no se puede vincular también estáticamente a MFC. Las aplicaciones se vinculan a archivos DLL de MFC estándar vinculados dinámicamente a MFC igual que cualquier otro archivo DLL.

Los símbolos se suelen exportar desde un archivo DLL de MFC estándar mediante la interfaz estándar de C. La declaración de una función exportada desde un archivo DLL de MFC estándar tiene un aspecto similar al siguiente:

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Todas las asignaciones de memoria de un archivo DLL de MFC estándar deben permanecer dentro del archivo DLL; este no debe pasar ni recibir ninguno de los elementos siguientes del ejecutable que realiza la llamada:

- Punteros a objetos de MFC

- Punteros a memoria asignada por MFC

Si necesita alguno de estos elementos o tiene que pasar objetos derivados de MFC entre el archivo ejecutable que realiza la llamada y el archivo DLL, tendrá que generar un archivo DLL de extensión de MFC.

Es seguro pasar punteros a la memoria asignados por las bibliotecas en tiempo de ejecución de C entre una aplicación y un archivo DLL solo si realiza una copia de los datos. No debe eliminar ni cambiar el tamaño de estos punteros, ni usarlos sin hacer una copia de la memoria.

Al compilar un archivo DLL de MFC estándar que se vincula dinámicamente a MFC, debe usar la macro [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) para cambiar el estado del módulo MFC correctamente. Para hacerlo, agregue la línea de código siguiente al principio de las funciones exportadas desde el archivo DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

La macro **AFX_MANAGE_STATE** no se debe usar en archivos DLL de MFC estándar que se vinculen estáticamente a MFC ni en archivos DLL de extensión de MFC. Para obtener más información, vea [Administrar los datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md).

Para obtener un ejemplo de cómo escribir, compilar y usar un archivo DLL de MFC estándar, vea el ejemplo [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap). Para obtener más información sobre los archivos DLL de MFC estándar que se vinculan dinámicamente a MFC, vea en el resumen del ejemplo la sección titulada "Convertir DLLScreenCap para vincular dinámicamente con el archivo DLL de MFC".

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Inicialización de archivos DLL de MFC estándar](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Estados de módulos de un archivo DLL de MFC estándar vinculado dinámicamente a MFC](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)

- [Administración de datos de estado de los módulos MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

- [Uso de archivos DLL de extensión MFC de base de datos, OLE y Sockets en archivos DLL de MFC estándar](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Uso de MFC como parte de un archivo DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

## <a name="see-also"></a>Vea también

[Tipos de archivos DLL](kinds-of-dlls.md)
