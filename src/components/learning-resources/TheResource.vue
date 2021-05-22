<template>
    <div>
        <base-card>
            <base-button 
                @click="setSelectedTab('add-resource')" 
                :mode="addButtomMode"
                >Add Resource</base-button>
            <base-button 
                @click="setSelectedTab('stored-resources')"
                :mode="storedResButtomMode"
                >Stored Resource</base-button>
        </base-card>
        <component :is="selectedTab"></component>
    </div>
</template>

<script>
import AddResource from './AddResource';
import StoredResources from './StoredResources';
export default {
    components: {
        AddResource,
        StoredResources,
    },
    data() {
        return {
            selectedTab: 'stored-resources',
            storedResources: [
                {id: 'official-guide', title: 'Official Guide', description: 'The official VueJS documentation', link: 'https://vuejs.org'},
                {id: 'google', title: 'Google', description: 'Learn to Google...', link: 'https://google.com'}
            ]
        };
    },
    provide() {
        return {
            resources: this.storedResources
        };
    },
    computed: {
        storedResButtomMode() {
            return this.selectedTab === 'stored-resources' ? '' : 'flat';
        },
        addButtomMode() {
            return this.selectedTab === 'add-resource' ? '' : 'flat';
        },
    },
    methods: {
        setSelectedTab(tab) {
            this.selectedTab = tab;
        },
    },
}
</script>

