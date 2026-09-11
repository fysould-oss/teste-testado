# teste-testado
https://dontpad.com/20262_pam2_mongagua

import React, { useState } from "react";
import {
  Pressable,
  ScrollView,
  StatusBar,
  StyleSheet,
  Text,
  View,
} from "react-native";

export default function HomeScreen() {
  // Mudança principal: O estado agora guarda o NOME do dia (string) ou null
  const [aberto, setAberto] = useState<string | null>(null);

  // Função para facilitar a troca (toggle)
  const toggleDia = (dia: string) => {
    // Se o dia clicado já estiver aberto, ele fecha (null).
    // Se for um dia novo, ele abre o novo e fecha o anterior.
    setAberto(aberto === dia ? null : dia);
  };

  return (
    <View style={styles.background}>
      <StatusBar barStyle="light-content" />

      <ScrollView
        style={styles.background}
        contentContainerStyle={styles.container}
      >
        <Text style={styles.titulo}>ETEC Adolpho Berezin</Text>

        <View style={styles.card}>
          <Text style={styles.subtitulo}>Desenvolvimento de Sistemas</Text>
          <Text style={styles.descricao}>
            Curso completo para desenvolvedores desktop, web e mobile
          </Text>
        </View>

        <Text style={styles.textoFundo}>Informações Gerais do Curso</Text>

        {/* --- TABELA FIXA: FICHA TÉCNICA --- */}
        <View style={styles.fichaTecnica}>
          <View style={styles.fichaLinha}>
            <Text style={styles.fichaLabel}>Carga Horária Total:</Text>
            <Text style={styles.fichaValor}>1.200h</Text>
          </View>
          <View style={styles.fichaLinha}>
            <Text style={styles.fichaLabel}>Parte Técnica:</Text>
            <Text style={styles.fichaValor}>800h</Text>
          </View>
          <View style={styles.fichaLinha}>
            <Text style={styles.fichaLabel}>Base Comum:</Text>
            <Text style={styles.fichaValor}>400h</Text>
          </View>
          <View style={styles.fichaLinha}>
            <Text style={styles.fichaLabel}>Período:</Text>
            <Text style={styles.fichaValor}>Vespertino</Text>
          </View>
          <View style={styles.fichaLinhaSemBorda}>
            <Text style={styles.fichaLabel}>Horário:</Text>
            <Text style={styles.fichaValor}>Seg a Sex das 13:30 às 18:50</Text>
          </View>
        </View>

        <Text style={styles.textoFundo}>
          Toque abaixo para ver o horário diário
        </Text>

        {/* --- ACORDEON: Primeiro Ano --- */}
        <View style={styles.tabelaContainer}>
          <Pressable
            style={[
              styles.linhaHeader,
              aberto === "segunda" && styles.linhaHeaderAberta,
            ]}
            onPress={() => toggleDia("segunda")}
          >
            <Text style={[styles.colunaHoraHeader, styles.textoHeader]}>
              Primeiro Ano - 1MDS
            </Text>
            <Text style={[styles.colunaMateriaHeader, styles.textoHeader]}>
              {aberto === "segunda" ? "▲" : "▼"}
            </Text>
          </Pressable>

          {aberto === "segunda" && (
            <View style={styles.corpoAcordeon}>
              <View style={styles.linhaTabela}>
                <View style={styles.colunaHora}>
                  <Text style={styles.textoHora}>L.P.</Text>
                </View>
                <View style={styles.colunaMateria}>
                  <Text style={styles.textoMateria}>Lingua Portuguesa</Text>
                  <Text style={styles.textoProfessor}>Profª. Meire</Text>
                </View>
              </View>
              <View style={styles.linhaTabela}>
                <View style={styles.colunaHora}>
                  <Text style={styles.textoHora}>L.I.</Text>
                </View>
                <View style={styles.colunaMateria}>
                  <Text style={styles.textoMateria}>Lingua Inglesa</Text>
                  <Text style={styles.textoProfessor}>Profª. Meire</Text>
                </View>
              </View>
              <View style={styles.linhaIntervalo}>
                <Text style={styles.textoIntervalo}>15:10 - INTERVALO</Text>
              </View>
              <View style={styles.linhaTabela}>
                <View style={styles.colunaHora}>
                  <Text style={styles.textoHora}>15:30</Text>
                </View>
                <View style={styles.colunaMateria}>
                  <Text style={styles.textoMateria}>PW III</Text>
                  <Text style={styles.textoProfessor}>Prof. Fulano</Text>
                </View>
              </View>
            </View>
          )}
        </View>

        {/* --- ACORDEON: TERÇA-FEIRA --- */}
        <View style={styles.tabelaContainer}>
          <Pressable
            style={[
              styles.linhaHeader,
              aberto === "terca" && styles.linhaHeaderAberta,
            ]}
            onPress={() => toggleDia("terca")}
          >
            <Text style={[styles.colunaHoraHeader, styles.textoHeader]}>
              TERÇA - FEIRA
            </Text>
            <Text style={[styles.colunaMateriaHeader, styles.textoHeader]}>
              {aberto === "terca" ? "▲" : "▼"}
            </Text>
          </Pressable>

          {aberto === "terca" && (
            <View style={styles.corpoAcordeon}>
              <View style={styles.linhaTabela}>
                <View style={styles.colunaHora}>
                  <Text style={styles.textoHora}>13:30</Text>
                </View>
                <View style={styles.colunaMateria}>
                  <Text style={styles.textoMateria}>Banco de Dados</Text
                  <Text style={styles.textoProfessor}>Prof. Ciclano</Text>
                </View>
              </View>
              <View style={styles.linhaIntervalo}>
                <Text style={styles.textoIntervalo}>15:10 - INTERVALO</Text>
              </View>
              <View style={styles.linhaTabela}>
                <View style={styles.colunaHora}>
                  <Text style={styles.textoHora}>15:30</Text>
                </View>
                <View style={styles.colunaMateria}>
                  <Text style={styles.textoMateria}>Sistemas Embarcados</Text>
                  <Text style={styles.textoProfessor}>Prof. Beltrano</Text>
                </View>
              </View>
            </View>
          )}
        </View>

        {/* Repetir a mesma lógica para Quarta, Quinta e Sexta trocando apenas a string no toggleDia e no teste do && */}
      </ScrollView>
    </View>
  );
}

const styles = StyleSheet.create({
  background: {
    flex: 1,
    backgroundColor: "#001a33",
  },
  container: {
    flexGrow: 1,
    padding: 20,
    alignItems: "center",
    gap: 15,
  },
  titulo: {
    color: "#00d4ff",
    fontSize: 28,
    fontWeight: "bold",
    marginTop: 40,
  },
  card: {
    backgroundColor: "rgba(255, 255, 255, 0.1)",
    padding: 20,
    borderRadius: 15,
    width: "100%",
    alignItems: "center",
    borderWidth: 1,
    borderColor: "#00d4ff",
  },
  subtitulo: {
    color: "#FFF",
    fontSize: 20,
    fontWeight: "600",
  },
  descricao: {
    color: "#ccc",
    textAlign: "center",
    marginTop: 10,
  },
  textoFundo: {
    color: "#555",
    fontSize: 12,
    textTransform: "uppercase",
    marginTop: 10,
    textAlign: "center",
  },
  fichaTecnica: {
    backgroundColor: "rgba(0, 212, 255, 0.05)",
    width: "100%",
    borderRadius: 12,
    padding: 15,
    borderWidth: 1,
    borderColor: "rgba(0, 212, 255, 0.3)",
  },
  fichaLinha: {
    flexDirection: "row",
    justifyContent: "space-between",
    paddingVertical: 8,
    borderBottomWidth: 1,
    borderBottomColor: "rgba(255, 255, 255, 0.1)",
  },
  fichaLinhaSemBorda: {
    flexDirection: "row",
    justifyContent: "space-between",
    paddingVertical: 8,
  },
  fichaLabel: {
    color: "#00d4ff",
    fontWeight: "bold",
    fontSize: 14,
  },
  fichaValor: {
    color: "#FFF",
    fontSize: 14,
    textAlign: "right",
    flex: 1,
    marginLeft: 10,
  },
  tabelaContainer: {
    width: "100%",
    marginBottom: 10,
  },
  linhaHeader: {
    flexDirection: "row",
    backgroundColor: "rgba(0, 212, 255, 0.15)",
    padding: 15,
    borderRadius: 10,
    borderWidth: 1,
    borderColor: "#00d4ff",
    justifyContent: "space-between",
  },
  linhaHeaderAberta: {
    borderBottomLeftRadius: 0,
    borderBottomRightRadius: 0,
    backgroundColor: "rgba(0, 212, 255, 0.3)",
  },
  corpoAcordeon: {
    backgroundColor: "rgba(255, 255, 255, 0.03)",
    borderWidth: 1,
    borderTopWidth: 0,
    borderColor: "#00d4ff",
    borderBottomLeftRadius: 10,
    borderBottomRightRadius: 10,
  },
  colunaHoraHeader: { fontWeight: "bold", color: "#00d4ff" },
  colunaMateriaHeader: { color: "#00d4ff", fontWeight: "bold" },
  textoHeader: {
    color: "#00d4ff",
    fontWeight: "bold",
    fontSize: 13,
  },
  linhaTabela: {
    flexDirection: "row",
    paddingVertical: 12,
    borderBottomWidth: 1,
    borderBottomColor: "rgba(255, 255, 255, 0.05)",
  },
  colunaHora: {
    width: "25%",
    alignItems: "center",
    justifyContent: "center",
  },
  colunaMateria: {
    width: "75%",
    paddingLeft: 15,
  },
  textoHora: {
    color: "#00d4ff",
    fontSize: 16,
    fontWeight: "bold",
  },
  textoMateria: {
    color: "#FFF",
    fontSize: 15,
  },
  textoProfessor: {
    color: "#888",
    fontSize: 12,
  },
  linhaIntervalo: {
    backgroundColor: "rgba(255, 255, 255, 0.05)",
    padding: 6,
    alignItems: "center",
  },
  textoIntervalo: {
    color: "#ffcc00",
    fontSize: 11,
    fontWeight: "bold",
  },
});
