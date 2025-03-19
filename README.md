# Jimenez_Beronica_Actividad2
Caso de Estudio: CompuWork- Sistema de Gestión de Recursos Humanos

import java.util.*;

// Clase base Empleado
abstract class Empleado {
    protected int id;
    protected String nombre;
    protected String cargo;
    protected double salario;

    public Empleado(int id, String nombre, String cargo, double salario) {
        this.id = id;
        this.nombre = nombre;
        this.cargo = cargo;
        this.salario = salario;
    }
    
    public abstract void calcularBonificacion();
    
    public void mostrarInformacion() {
        System.out.println("ID: " + id + ", Nombre: " + nombre + ", Cargo: " + cargo + ", Salario: " + salario);
    }
}

// Subclase Empleado Permanente
class EmpleadoPermanente extends Empleado {
    private double beneficios;
    
    public EmpleadoPermanente(int id, String nombre, String cargo, double salario, double beneficios) {
        super(id, nombre, cargo, salario);
        this.beneficios = beneficios;
    }
    
    @Override
    public void calcularBonificacion() {
        System.out.println("Bonificación de " + nombre + ": " + (salario * 0.1 + beneficios));
    }
}

// Subclase Empleado Temporal
class EmpleadoTemporal extends Empleado {
    private int duracionContrato;
    
    public EmpleadoTemporal(int id, String nombre, String cargo, double salario, int duracionContrato) {
        super(id, nombre, cargo, salario);
        this.duracionContrato = duracionContrato;
    }
    
    @Override
    public void calcularBonificacion() {
        System.out.println("Bonificación de " + nombre + ": " + (salario * 0.05));
    }
}

// Clase Departamento
class Departamento {
    private String nombre;
    private List<Empleado> empleados;
    
    public Departamento(String nombre) {
        this.nombre = nombre;
        this.empleados = new ArrayList<>();
    }
    
    public void agregarEmpleado(Empleado empleado) {
        empleados.add(empleado);
    }
    
    public void mostrarEmpleados() {
        System.out.println("Empleados en " + nombre + ":");
        for (Empleado e : empleados) {
            e.mostrarInformacion();
        }
    }
}

// Clase Reporte de Desempeño
class ReporteDesempeño {
    public static void generarReporte(Empleado empleado) {
        System.out.println("Generando reporte de desempeño para: " + empleado.nombre);
    }
}
