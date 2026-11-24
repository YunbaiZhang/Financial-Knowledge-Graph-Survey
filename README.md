# Financial Knowledge Graph Survey

A filing says that Company A bought 10% of Company B. An extractor proposes the relationship “A acquired B.” An LLM agent checks the filing and records the narrower claim that A owns a 10% stake in B. That distinction matters when an analyst later searches the graph for acquisitions.

This reading guide accompanies *Knowledge Graphs for Financial Analysis in the Era of LLM Agents: A Survey*. It follows how financial evidence enters a graph, changes over time, and informs decisions such as comparing savings rates or interpreting an earnings call.

[Taxonomy and selected papers](#taxonomy-and-selected-papers) · [Evaluation](#evaluation) · [Datasets and benchmarks](#datasets-and-benchmarks)

[![Four financial workflows compare how a fixed pipeline and an agent handle an ownership stake, a ticker change, a dividend, and a savings-rate comparison.](figures/workflows.png)](figures/workflows.png)

*Figure 2 from the survey. In the last example, the graph identifies the customer’s bank but lacks both savings rates. The agent retrieves the two quotes and finds a one-percentage-point difference. The rates are hypothetical.*

## Taxonomy and selected papers

[![The five branches of the survey taxonomy connect financial knowledge graph tasks to subtopics and representative studies.](figures/taxonomy.png)](figures/taxonomy.png)

*Figure 1 from the survey. Each branch groups studies by the problem they address. A system can contribute to more than one branch.*

### 1. Knowledge graph construction

- **FinReflectKG** extracts relationships from annual 10-K filings and revisits each proposed triple against the source passage and financial schema. [Paper](https://arxiv.org/abs/2508.17906) · [Dataset](https://huggingface.co/datasets/domyn/FinReflectKG)
- **FinKario** connects company fundamentals with market events extracted from equity research reports. [Paper](https://aclanthology.org/2026.acl-long.446/) · [Code](https://github.com/Jackson906E/FinKario)

### 2. Temporal evolution

- **The Company Control Problem, Reactively** traces how a change in one ownership stake can alter which companies a shareholder controls indirectly. [Paper](https://ceur-ws.org/Vol-3478/paper24.pdf)
- **FIRME** links different names for the same entity across investor records and tracks how an investor’s interests change over time. [Paper](https://arxiv.org/abs/2610.40482)

### 3. Verification, reconciliation, and admission

A proposed graph update raises three questions. Does the evidence support the claim? Do the records refer to the same entity? Should the update enter the shared graph?

- **AuditFlow** checks figures in structured financial filings against executable accounting rules. [Paper](https://arxiv.org/abs/2606.03031)
- **GraLMatch** matches company and security records across providers and examines how an incorrect match can join unrelated records into one group. [Paper](https://openproceedings.org/2025/conf/edbt/paper-10.pdf)

### 4. Adaptive acquisition

- **RiskTagger** uses evidence from a Web3 incident to decide which transaction paths to investigate next. [Paper](https://arxiv.org/abs/2510.17848)

### 5. Knowledge graph usage

- **RAG-FLARKO** uses an investor’s past trades to select market price histories for asset recommendations. [Paper](https://ceur-ws.org/Vol-4079/paper8.pdf)
- **CARAG** queries a temporal graph to compare an earnings disclosure with the company’s own history and its peers when forecasting post-earnings price movements. [Paper](https://aclanthology.org/2026.eacl-long.141/)

## Evaluation

[![Four evaluation branches cover graph structure and evidence, downstream financial tasks, graph-guided retrieval and reasoning, and reliability over time.](figures/evaluation.png)](figures/evaluation.png)

*Figure 6 from the survey. The four branches ask different questions about the same system.*

| Dimension | A question to test |
| --- | --- |
| Structural and evidential quality | Does the source support the relationship, and which important facts did extraction miss? |
| Downstream task utility | Does using the graph improve the answer, recommendation, or forecast on a financial task? |
| Graph-guided retrieval and reasoning | Did the agent find the right filing and use its evidence to justify the conclusion? |
| Longitudinal reliability | Can the system reproduce an earlier answer using only information available on that date, and revisit affected conclusions after a correction? |

## Datasets and benchmarks

| Resource | What readers can use it for | Links |
| --- | --- | --- |
| **REFinD** | Evaluate relation extraction against human annotations in SEC filings. | [Project and data](https://refind-re.github.io/) |
| **FinReflectKG–EvalBench** | Compare extracted 10-K facts with their source passages and assess how much relevant information the graph captures. | [Paper](https://arxiv.org/abs/2510.05710) · [Data](https://huggingface.co/datasets/domyn/FinReflectKG-EvalBench) |
| **FAR-Trans** | Use historical customer transactions and asset prices to evaluate investment recommendations. | [Data](https://researchdata.gla.ac.uk/1658/) · [Code](https://github.com/JavierSanzCruza/far-trans) |
| **TempFinRAG** | Test whether a financial question-answering system respects what was public before and after a filing date. | [Paper](https://www.mdpi.com/2073-8994/18/9/1498) |
