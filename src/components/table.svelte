<script>
	import {
		Table,
		TableBody,
		TableBodyCell,
		TableBodyRow,
		TableHead,
		TableHeadCell,
		TableSearch
	} from 'flowbite-svelte';
	let searchTerm = '';
	let items = [
		'3,90',
		'3,90',
		'3,89',
		'3,88',
		'3,87',
		'3,87',
		'3,87',
		'3,86',
		'3,86',
		'3,86',
		'3,85',
		'3,84',
		'3,83',
		'3,83',
		'3,82',
		'3,81',
		'3,81',
		'3,80',
		'3,80',
		'3,80',
		'3,80',
		'3,79',
		'3,79',
		'3,77',
		'3,76',
		'3,76',
		'3,76',
		'3,76',
		'3,75',
		'3,75',
		'3,75',
		'3,74',
		'3,74',
		'3,73',
		'3,73',
		'3,72',
		'3,72',
		'3,72',
		'3,71',
		'3,71',
		'3,71',
		'3,70',
		'3,69',
		'3,69',
		'3,68',
		'3,68',
		'3,68',
		'3,68',
		'3,68',
		'3,67',
		'3,67',
		'3,66',
		'3,66',
		'3,65',
		'3,65',
		'3,65',
		'3,65',
		'3,64',
		'3,63',
		'3,63',
		'3,62',
		'3,62',
		'3,60',
		'3,60',
		'3,60',
		'3,60',
		'3,60',
		'3,60',
		'3,59',
		'3,59',
		'3,59',
		'3,59',
		'3,59',
		'3,59',
		'3,58',
		'3,58',
		'3,58',
		'3,58',
		'3,55',
		'3,54',
		'3,54',
		'3,54',
		'3,54',
		'3,53',
		'3,53',
		'3,53',
		'3,52',
		'3,51',
		'3,51',
		'3,50',
		'3,50',
		'3,50',
		'3,50',
		'3,48',
		'3,48',
		'3,47',
		'3,46',
		'3,45',
		'3,45',
		'3,44',
		'3,44',
		'3,44',
		'3,44',
		'3,43',
		'3,42',
		'3,41',
		'3,41',
		'3,40',
		'3,40',
		'3,40',
		'3,40',
		'3,40',
		'3,40',
		'3,39',
		'3,39',
		'3,39',
		'3,39',
		'3,38',
		'3,38',
		'3,37',
		'3,37',
		'3,36',
		'3,34',
		'3,34',
		'3,32',
		'3,32',
		'3,31',
		'3,30',
		'3,30',
		'3,28',
		'3,28',
		'3,26',
		'3,26',
		'3,24',
		'3,23',
		'3,22',
		'3,20',
		'3,20',
		'3,20',
		'3,19',
		'3,19',
		'3,18',
		'3,17',
		'3,16',
		'3,14',
		'3,13',
		'3,12',
		'3,05',
		'2,98',
		'2,94',
		'2,78',
		'2,76'
	];
    const ipkIdMap = new Map();
    const irr = items.map((ipk, index)=>({
        id: index+1,
        ipk: ipk,
    })).map((obj)=> {
        const {id,ipk} =obj;
        const existingId = ipkIdMap.get(ipk);
        if (existingId !== undefined){
            return {id:existingId, ipk}
        } else {
            ipkIdMap.set(ipk, id);
            return obj;
        }
    })
	$: filteredItems = irr.filter(
		(item) => item.ipk.toLowerCase().indexOf(searchTerm.toLowerCase()) !== -1
	);
</script>

<TableSearch striped={true} placeholder="Search by IPK" hoverable={true} bind:inputValue={searchTerm}>
	<TableHead class="text-center">
		<TableHeadCell>👑</TableHeadCell>
		<TableHeadCell>IPK</TableHeadCell>
	</TableHead>
	<TableBody class="divide-y">
		{#each filteredItems as i}
			<TableBodyRow class="text-center">
				<TableBodyCell >{i.id}</TableBodyCell>
				<TableBodyCell>{i.ipk}</TableBodyCell>
			</TableBodyRow>
		{/each}
	</TableBody>
</TableSearch>
