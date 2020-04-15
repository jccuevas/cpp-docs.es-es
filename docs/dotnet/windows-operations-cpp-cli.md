---
title: Operaciones de Windows (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows [C++], Windows-specific tasks
- .NET Framework [C++], Windows operations
- Visual C++, Windows operations
- Windows operations [C++]
- .NET Framework, shutdown
- shutdown
- termination
- applications [C++], shutdown
- Visual C++, user interactive state
- user interactive state
- Visual C++, reading from Windows Registry
- registry, reading
- performance counters
- performance counters, reading Windows performance counters
- performance monitoring, Windows performance counters
- performance, counters
- counters, reading Windows performance counters
- performance
- performance monitoring
- text, retrieving from Clipboard
- Clipboard, retrieving text
- current user names
- user names, retrieving
- UserName string
- .NET Framework, version
- Version property, retrieving .NET Framework version
- computer name, retrieving
- machine name, retrieving
- computer name
- Windows [C++], version
- Windows [C++], retrieving version using Visual C++
- time, elapsed since startup
- counters, elapsed time
- startup, time elapsed since
- tick counts
- startup
- text, storing in Clipboard
- Clipboard, storing text
- registry, writing to
- Visual C++, writing to Windows Registry
ms.assetid: b9a75cb4-0589-4d5b-92cb-5e8be42b4ac0
ms.openlocfilehash: 99fce804ad30e01bdbaa99b1636a5238ff535f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371772"
---
# <a name="windows-operations-ccli"></a>Operaciones de Windows (C++/CLI)

Muestra varias tareas específicas de Windows mediante el Windows SDK.

En los temas siguientes se muestran varias operaciones de Windows realizadas con Windows SDK mediante Visual C++.

## <a name="determine-if-shutdown-has-started"></a><a name="determine_shutdown"></a>Determinar si se ha iniciado el apagado

En el ejemplo de código siguiente se muestra cómo determinar si la aplicación o .NET Framework está terminando actualmente. Esto es útil para tener acceso a elementos estáticos en .NET Framework porque, durante el apagado, el sistema finaliza estas construcciones y no se pueden usar de forma fiable. Al comprobar <xref:System.Environment.HasShutdownStarted%2A> primero la propiedad, puede evitar posibles errores al no tener acceso a estos elementos.

### <a name="example"></a>Ejemplo

```cpp
// check_shutdown.cpp
// compile with: /clr
using namespace System;
int main()
{
   if (Environment::HasShutdownStarted)
      Console::WriteLine("Shutting down.");
   else
      Console::WriteLine("Not shutting down.");
   return 0;
}
```

## <a name="determine-the-user-interactive-state"></a><a name="determine_user"></a>Determinar el estado interactivo del usuario

En el ejemplo de código siguiente se muestra cómo determinar si el código se está ejecutando en un contexto interactivo del usuario. Si <xref:System.Environment.UserInteractive%2A> es false, el código se ejecuta como un proceso de servicio o desde dentro de una aplicación web, en cuyo caso no debe intentar interactuar con el usuario.

### <a name="example"></a>Ejemplo

```cpp
// user_interactive.cpp
// compile with: /clr
using namespace System;

int main()
{
   if ( Environment::UserInteractive )
      Console::WriteLine("User interactive");
   else
      Console::WriteLine("Noninteractive");
   return 0;
}
```

## <a name="read-data-from-the-windows-registry"></a><a name="read_registry"></a>Leer datos del Registro de Windows

El ejemplo de código siguiente utiliza la clave <xref:Microsoft.Win32.Registry.CurrentUser> para leer los datos del Registro de Windows. En primer lugar, las subclaves se enumeran mediante el <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> método <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> y, a continuación, la subclave Identities se abre mediante el método. Del mismo modo que las claves raíz, cada subclave se representa mediante la clase <xref:Microsoft.Win32.RegistryKey>. Finalmente, el nuevo objeto <xref:Microsoft.Win32.RegistryKey> se utiliza para enumerar los pares clave/valor.

### <a name="example"></a>Ejemplo

```cpp
// registry_read.cpp
// compile with: /clr
using namespace System;
using namespace Microsoft::Win32;

int main( )
{
   array<String^>^ key = Registry::CurrentUser->GetSubKeyNames( );

   Console::WriteLine("Subkeys within CurrentUser root key:");
   for (int i=0; i<key->Length; i++)
   {
      Console::WriteLine("   {0}", key[i]);
   }

   Console::WriteLine("Opening subkey 'Identities'...");
   RegistryKey^ rk = nullptr;
   rk = Registry::CurrentUser->OpenSubKey("Identities");
   if (rk==nullptr)
   {
      Console::WriteLine("Registry key not found - aborting");
      return -1;
   }

   Console::WriteLine("Key/value pairs within 'Identities' key:");
   array<String^>^ name = rk->GetValueNames( );
   for (int i=0; i<name->Length; i++)
   {
      String^ value = rk->GetValue(name[i])->ToString();
      Console::WriteLine("   {0} = {1}", name[i], value);
   }

   return 0;
}
```

### <a name="remarks"></a>Observaciones

La clase <xref:Microsoft.Win32.Registry> es simplemente un contenedor para instancias estáticas de <xref:Microsoft.Win32.RegistryKey>. Cada instancia representa un nodo de Registro raíz. Las instancias son <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine> y <xref:Microsoft.Win32.Registry.Users>.

Además de ser estáticos, los objetos incluidos en la clase <xref:Microsoft.Win32.Registry> son de sólo lectura. Por otra parte, las instancias de la clase <xref:Microsoft.Win32.RegistryKey> que se crean para tener acceso al contenido de los objetos del Registro también son de sólo lectura. Para obtener un ejemplo de cómo invalidar este comportamiento, vea Cómo: escribir datos en el Registro de [Windows (C++/CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md).

Hay dos objetos adicionales en la clase <xref:Microsoft.Win32.Registry>: <xref:Microsoft.Win32.Registry.DynData> y <xref:Microsoft.Win32.Registry.PerformanceData>. Los dos son instancias de la clase <xref:Microsoft.Win32.RegistryKey>. El <xref:Microsoft.Win32.Registry.DynData> objeto contiene información dinámica del Registro, que solo se admite en Windows 98 y Windows Me. El objeto <xref:Microsoft.Win32.Registry.PerformanceData> se puede usar para tener acceso a información del contador de rendimiento para aplicaciones que usan el sistema de supervisión de rendimiento de Windows. El <xref:Microsoft.Win32.Registry.PerformanceData> nodo representa información que no se almacena realmente en el registro y, por lo tanto, no se puede ver mediante Regedit.exe.

## <a name="read-windows-performance-counters"></a><a name="read_performance"></a>Leer contadores de rendimiento de Windows

Algunas aplicaciones y subsistemas de Windows exponen los datos de rendimiento a través del sistema de rendimiento de Windows. Se puede tener acceso <xref:System.Diagnostics.PerformanceCounterCategory> a <xref:System.Diagnostics.PerformanceCounter> estos contadores <xref:System.Diagnostics?displayProperty=fullName> mediante las clases y, que residen en el espacio de nombres.

En el ejemplo de código siguiente se usan estas clases para recuperar y mostrar un contador que Windows actualiza para indicar el porcentaje de tiempo que el procesador está ocupado.

> [!NOTE]
> Este ejemplo exige privilegios administrativos para ejecutarse en Windows Vista.

### <a name="example"></a>Ejemplo

```cpp
// processor_timer.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::Threading;
using namespace System::Diagnostics;
using namespace System::Timers;

ref struct TimerObject
{
public:
   static String^ m_instanceName;
   static PerformanceCounter^ m_theCounter;

public:
   static void OnTimer(Object^ source, ElapsedEventArgs^ e)
   {
      try
      {
         Console::WriteLine("CPU time used: {0,6} ",
          m_theCounter->NextValue( ).ToString("f"));
      }
      catch(Exception^ e)
      {
         if (dynamic_cast<InvalidOperationException^>(e))
         {
            Console::WriteLine("Instance '{0}' does not exist",
                  m_instanceName);
            return;
         }
         else
         {
            Console::WriteLine("Unknown exception... ('q' to quit)");
            return;
         }
      }
   }
};

int main()
{
   String^ objectName = "Processor";
   String^ counterName = "% Processor Time";
   String^ instanceName = "_Total";

   try
   {
      if ( !PerformanceCounterCategory::Exists(objectName) )
      {
         Console::WriteLine("Object {0} does not exist", objectName);
         return -1;
      }
   }
   catch (UnauthorizedAccessException ^ex)
   {
      Console::WriteLine("You are not authorized to access this information.");
      Console::Write("If you are using Windows Vista, run the application with ");
      Console::WriteLine("administrative privileges.");
      Console::WriteLine(ex->Message);
      return -1;
   }

   if ( !PerformanceCounterCategory::CounterExists(
          counterName, objectName) )
   {
      Console::WriteLine("Counter {0} does not exist", counterName);
      return -1;
   }

   TimerObject::m_instanceName = instanceName;
   TimerObject::m_theCounter = gcnew PerformanceCounter(
          objectName, counterName, instanceName);

   System::Timers::Timer^ aTimer = gcnew System::Timers::Timer();
   aTimer->Elapsed += gcnew ElapsedEventHandler(&TimerObject::OnTimer);
   aTimer->Interval = 1000;
   aTimer->Enabled = true;
   aTimer->AutoReset = true;

   Console::WriteLine("reporting CPU usage for the next 10 seconds");
   Thread::Sleep(10000);
   return 0;
}
```

## <a name="retrieve-text-from-the-clipboard"></a><a name="retrieve_text"></a>Recuperar texto del Portapapeles

En el ejemplo <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> de código siguiente se <xref:System.Windows.Forms.IDataObject> utiliza la función miembro para devolver un puntero a la interfaz. Esta interfaz se puede consultar para el formato de los datos y se utiliza para recuperar los datos reales.

### <a name="example"></a>Ejemplo

```cpp
// read_clipboard.cpp
// compile with: /clr
#using <system.dll>
#using <system.Drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;

[STAThread] int main( )
{
   IDataObject^ data = Clipboard::GetDataObject( );

   if (data)
   {
      if (data->GetDataPresent(DataFormats::Text))
      {
         String^ text = static_cast<String^>
           (data->GetData(DataFormats::Text));
         Console::WriteLine(text);
      }
      else
         Console::WriteLine("Nontext data is in the Clipboard.");
   }
   else
   {
      Console::WriteLine("No data was found in the Clipboard.");
   }

   return 0;
}
```

## <a name="retrieve-the-current-username"></a><a name="retrieve_current"></a>Recuperar el nombre de usuario actual

En el ejemplo de código siguiente se muestra la recuperación del nombre de usuario actual (el nombre del usuario que ha iniciado sesión en Windows). El nombre se <xref:System.Environment.UserName%2A> almacena en la cadena, que se define en el <xref:System.Environment> espacio de nombres.

### <a name="example"></a>Ejemplo

```cpp
// username.cpp
// compile with: /clr
using namespace System;

int main()
{
   Console::WriteLine("\nCurrent user: {0}", Environment::UserName);
   return 0;
}
```

## <a name="retrieve-the-net-framework-version"></a><a name="retrieve_dotnet"></a>Recuperar la versión de .NET Framework

En el ejemplo de código siguiente se muestra cómo determinar <xref:System.Environment.Version%2A> la versión de .NET Framework instalado actualmente con la propiedad, que es un puntero a un <xref:System.Version> objeto que contiene la información de versión.

### <a name="example"></a>Ejemplo

```cpp
// dotnet_ver.cpp
// compile with: /clr
using namespace System;
int main()
{
   Version^ version = Environment::Version;
   if (version)
   {
      int build = version->Build;
      int major = version->Major;
      int minor = version->Minor;
      int revision = Environment::Version->Revision;
      Console::Write(".NET Framework version: ");
      Console::WriteLine("{0}.{1}.{2}.{3}",
            build, major, minor, revision);
   }
   return 0;
}
```

## <a name="retrieve-the-local-machine-name"></a><a name="retrieve_local"></a>Recuperar el nombre de la máquina local

En el ejemplo de código siguiente se muestra la recuperación del nombre del equipo local (el nombre del equipo tal como aparece en una red). Puede lograr esto obteniendo la <xref:System.Environment.MachineName%2A> cadena, <xref:System.Environment> que se define en el espacio de nombres.

### <a name="example"></a>Ejemplo

```cpp
// machine_name.cpp
// compile with: /clr
using namespace System;

int main()
{
   Console::WriteLine("\nMachineName: {0}", Environment::MachineName);
   return 0;
}
```

## <a name="retrieve-the-windows-version"></a><a name="retrieve_version"></a>Recuperar la versión de Windows

En el ejemplo de código siguiente se muestra cómo recuperar la información de plataforma y versión del sistema operativo actual. Esta información se <xref:System.Environment.OSVersion%2A?displayProperty=fullName> almacena en la propiedad y consta de una enumeración <xref:System.Environment.Version%2A> que describe la versión de Windows en términos generales y un objeto que contiene la compilación exacta del sistema operativo.

### <a name="example"></a>Ejemplo

```cpp
// os_ver.cpp
// compile with: /clr
using namespace System;

int main()
{
   OperatingSystem^ osv = Environment::OSVersion;
   PlatformID id = osv->Platform;
   Console::Write("Operating system: ");

   if (id == PlatformID::Win32NT)
      Console::WriteLine("Win32NT");
   else if (id == PlatformID::Win32S)
      Console::WriteLine("Win32S");
   else if (id == PlatformID::Win32Windows)
      Console::WriteLine("Win32Windows");
   else
      Console::WriteLine("WinCE");

   Version^ version = osv->Version;
   if (version)
   {
      int build = version->Build;
      int major = version->Major;
      int minor = version->Minor;
      int revision = Environment::Version->Revision;
      Console::Write("OS Version: ");
      Console::WriteLine("{0}.{1}.{2}.{3}",
                   build, major, minor, revision);
   }

   return 0;
}
```

## <a name="retrieve-time-elapsed-since-startup"></a><a name="retrieve_time"></a>Recuperar el tiempo transcurrido desde el inicio

En el ejemplo de código siguiente se muestra cómo determinar el recuento de ticks o el número de milisegundos que han transcurrido desde que se inició Windows. Este valor se <xref:System.Environment.TickCount%2A?displayProperty=fullName> almacena en el miembro y, dado que es un valor de 32 bits, se restablece a cero aproximadamente cada 24,9 días.

### <a name="example"></a>Ejemplo

```cpp
// startup_time.cpp
// compile with: /clr
using namespace System;

int main( )
{
   Int32 tc = Environment::TickCount;
   Int32 seconds = tc / 1000;
   Int32 minutes = seconds / 60;
   float hours = static_cast<float>(minutes) / 60;
   float days = hours / 24;

   Console::WriteLine("Milliseconds since startup: {0}", tc);
   Console::WriteLine("Seconds since startup: {0}", seconds);
   Console::WriteLine("Minutes since startup: {0}", minutes);
   Console::WriteLine("Hours since startup: {0}", hours);
   Console::WriteLine("Days since startup: {0}", days);

   return 0;
}
```

## <a name="store-text-in-the-clipboard"></a><a name="store_text"></a>Almacenar texto en el Portapapeles

En el ejemplo <xref:System.Windows.Forms.Clipboard> de código <xref:System.Windows.Forms> siguiente se utiliza el objeto definido en el espacio de nombres para almacenar una cadena. Este objeto proporciona dos <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>funciones miembro: y . Los datos se almacenan en el Portapapeles enviando cualquier objeto derivado de <xref:System.Object> . <xref:System.Windows.Forms.Clipboard.SetDataObject%2A>

### <a name="example"></a>Ejemplo

```cpp
// store_clipboard.cpp
// compile with: /clr
#using <System.dll>
#using <System.Drawing.dll>
#using <System.Windows.Forms.dll>

using namespace System;
using namespace System::Windows::Forms;

[STAThread] int main()
{
   String^ str = "This text is copied into the Clipboard.";

   // Use 'true' as the second argument if
   // the data is to remain in the clipboard
   // after the program terminates.
   Clipboard::SetDataObject(str, true);

   Console::WriteLine("Added text to the Clipboard.");

   return 0;
}
```

## <a name="write-data-to-the-windows-registry"></a><a name="write_data"></a>Escribir datos en el registro de Windows

En el ejemplo <xref:Microsoft.Win32.Registry.CurrentUser> de código siguiente se utiliza <xref:Microsoft.Win32.RegistryKey> la clave para crear una instancia grabable de la clase correspondiente a la clave **Software.** El método <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A> se utiliza después para crear una nueva clave y agregarla a pares clave/valor.

### <a name="example"></a>Ejemplo

```cpp
// registry_write.cpp
// compile with: /clr
using namespace System;
using namespace Microsoft::Win32;

int main()
{
   // The second OpenSubKey argument indicates that
   // the subkey should be writable.
   RegistryKey^ rk;
   rk  = Registry::CurrentUser->OpenSubKey("Software", true);
   if (!rk)
   {
      Console::WriteLine("Failed to open CurrentUser/Software key");
      return -1;
   }

   RegistryKey^ nk = rk->CreateSubKey("NewRegKey");
   if (!nk)
   {
      Console::WriteLine("Failed to create 'NewRegKey'");
      return -1;
   }

   String^ newValue = "NewValue";
   try
   {
      nk->SetValue("NewKey", newValue);
      nk->SetValue("NewKey2", 44);
   }
   catch (Exception^)
   {
      Console::WriteLine("Failed to set new values in 'NewRegKey'");
      return -1;
   }

   Console::WriteLine("New key created.");
   Console::Write("Use REGEDIT.EXE to verify ");
   Console::WriteLine("'CURRENTUSER/Software/NewRegKey'\n");
   return 0;
}
```

### <a name="remarks"></a>Observaciones

Puede usar .NET Framework para tener <xref:Microsoft.Win32.Registry> acceso <xref:Microsoft.Win32.RegistryKey> al registro con las <xref:Microsoft.Win32> clases y, que se definen en el espacio de nombres. La clase **Registry** es un contenedor <xref:Microsoft.Win32.RegistryKey> para instancias estáticas de la clase. Cada instancia representa un nodo de Registro raíz. Las instancias son <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine> y <xref:Microsoft.Win32.Registry.Users>.

## <a name="related-sections"></a>Secciones relacionadas

<xref:System.Environment>

## <a name="see-also"></a>Consulte también

[Programación de .NET con C+/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
