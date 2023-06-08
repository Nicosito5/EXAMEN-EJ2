# EXAMEN-EJ2

import java.io.*;
import java.util.*;

class Libro {
    private String titulo;
    private String autor;
    private String identificador;
    private String categoria;
    private int edadRecomendada;
    private boolean prestado;

    public Libro(String titulo, String autor, String identificador, String categoria, int edadRecomendada) {
        this.titulo = titulo;
        this.autor = autor;
        this.identificador = identificador;
        this.categoria = categoria;
        this.edadRecomendada = edadRecomendada;
        this.prestado = false;
    }

    public String getTitulo() {
        return titulo;
    }

    public String getAutor() {
        return autor;
    }

    public String getIdentificador() {
        return identificador;
    }

    public String getCategoria() {
        return categoria;
    }

    public int getEdadRecomendada() {
        return edadRecomendada;
    }

    public boolean estaPrestado() {
        return prestado;
    }

    public void prestar() {
        prestado = true;
    }

    public void devolver() {
        prestado = false;
    }
}

class Usuario {
    private String nombre;
    private String apellido1;
    private String apellido2;
    private Date fechaNacimiento;
    private String dni;

    public Usuario(String nombre, String apellido1, String apellido2, Date fechaNacimiento, String dni) {
        this.nombre = nombre;
        this.apellido1 = apellido1;
        this.apellido2 = apellido2;
        this.fechaNacimiento = fechaNacimiento;
        this.dni = dni;
    }

    public String getNombre() {
        return nombre;
    }

    public String getApellido1() {
        return apellido1;
    }

    public String getApellido2() {
        return apellido2;
    }

    public Date getFechaNacimiento() {
        return fechaNacimiento;
    }

    public String getDni() {
        return dni;
    }
}


class SistemaPrestamos {
    private List<Libro> libros;
    private List<Usuario> usuarios;

    public SistemaPrestamos() {
        libros = new ArrayList<>();
        usuarios = new ArrayList<>();
    }

    public void agregarLibro(Libro libro) {
        libros.add(libro);
    }

    public void eliminarLibro(String identificador) {
        Libro libro = buscarLibro(identificador);
        if (libro != null) {
            libros.remove(libro);
        }
    }

    public void agregarUsuario(Usuario usuario) {
        usuarios.add(usuario);
    }

    public void eliminarUsuario(String dni) {
        Usuario usuario = buscarUsuario(dni);
        if (usuario != null) {
            usuarios.remove(usuario);
        }
    }

    public void prestarLibro(String identificador, String dni) {
        Libro libro = buscarLibro(identificador);
        Usuario usuario = buscarUsuario(dni);
        if (libro != null && usuario != null && !libro.estaPrestado() && usuarioPuedePrestarLibro(usuario, libro)) {
            libro.prestar();
            System.out.println("Libro prest
